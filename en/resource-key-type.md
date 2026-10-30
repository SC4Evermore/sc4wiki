---
title: "Resource Key Type"
description: ""
published: true
date: '2026-07-12T15:24:10Z'
tags: []
editor: markdown
dateCreated: '2008-09-20T15:35:07Z'
---

**Resource Key Type** (RKT) is a family of [Exemplar properties](/exemplar-properties) used to associate an exemplar with one or more models. Different RKT variants support different combinations of zoom levels, rotations, model states and offsets.

The primary properties are RKT0 through RKT5. A second set of mirrored properties, commonly identified by the `xm` suffix, uses the same formats.

## Overview

| Property | ID | Stored values | Purpose |
|----|----|----|----|
| RKT0 | `0x27812820` | 3 | One model for all zooms and rotations |
| RKT1 | `0x27812821` | 3 | Inferred model for each zoom and rotation |
| RKT2 | `0x27812822` | 22 | Explicit model IID for each zoom and rotation |
| RKT3 | `0x27812823` | 7 | Explicit model IID for each zoom |
| RKT4 | `0x27812824` | Multiples of 8 | Multiple models, offsets and model states |
| RKT5 | `0x27812825` | 3 | Inferred model for each zoom, rotation and state |

The game checks the primary properties in numerical order, beginning with RKT0. If an exemplar contains more than one primary RKT property, the first one found is used. Multiple primary RKT properties should therefore not be added to the same exemplar.

## Model instance numbering

RKT1, RKT2 and RKT5 use five zoom slots and four rotation slots. Internally, the model for a particular zoom and rotation is selected using:

    index = zoom slot × 4 + rotation slot

For inferred model families, the corresponding IID offsets are:

| Dimension  | IID offset        |
|------------|-------------------|
| Zoom/LOD   | `slot × 0x100`    |
| Rotation   | `slot × 0x10`     |
| RKT5 state | `state × 0x10000` |

The apparent compass direction of a rotation slot can be affected by the object's orientation and whether the mirrored RKT properties are being used.

## RKT0

RKT0 references one model for every zoom level and rotation. It contains one complete TGI:

    Rep 1: Type ID
    Rep 2: Group ID
    Rep 3: Instance ID

The stored IID is used without adding zoom or rotation offsets.

RKT0 is normally used for true 3D models, including some network pieces. Because the same model is shown at every zoom, fine geometry may appear excessively sharp or detailed at distant zoom levels.

Example:

    0x5AD0E817,0xBADB57F1,0x12345678

## RKT1

RKT1 references a conventional isometric model family containing one model for each of five zoom levels and four rotations, for a total of 20 models.

Only the base TGI is stored:

    Rep 1: Type ID
    Rep 2: Group ID
    Rep 3: Base Instance ID

The base IID normally identifies the first zoom and rotation model. The game derives the other model IIDs using:

    resolved IID = base IID + zoom offset + rotation offset

where:

    zoom offset     = zoom slot × 0x100
    rotation offset = rotation slot × 0x10

For a base IID of `0x12340000`, the model family occupies IIDs such as:

    0x12340000
    0x12340010
    0x12340020
    0x12340030

    0x12340100
    0x12340110
    ...
    0x12340430

RKT1 is used by most conventional buildings and props produced by the BAT.

## RKT2

RKT2 uses an explicit IID for every zoom and rotation. This permits models whose instance IDs do not follow the normal RKT1 naming scheme.

The property contains 22 values:

    Rep 1:  Type ID
    Rep 2:  Group ID
    Rep 3:  Zoom slot 0, rotation slot 0 IID
    Rep 4:  Zoom slot 0, rotation slot 1 IID
    Rep 5:  Zoom slot 0, rotation slot 2 IID
    Rep 6:  Zoom slot 0, rotation slot 3 IID
    Rep 7:  Zoom slot 1, rotation slot 0 IID
    ...
    Rep 22: Zoom slot 4, rotation slot 3 IID

The 20 explicit IIDs are arranged as five consecutive groups of four:

    IID index = 2 + zoom slot × 4 + rotation slot

RKT2 is sometimes described as having 20 values. This counts only the model IIDs and omits the shared Type and Group IDs. The complete property has 22 values.

RKT2 is used by some network models and other resources where the standard RKT1 IID pattern is unsuitable.

## RKT3

RKT3 references one true 3D model for each zoom level. Rotation does not select a different resource.

The property contains seven values:

    Rep 1: Type ID
    Rep 2: Group ID
    Rep 3: Zoom slot 0 IID
    Rep 4: Zoom slot 1 IID
    Rep 5: Zoom slot 2 IID
    Rep 6: Zoom slot 3 IID
    Rep 7: Zoom slot 4 IID

The game selects the IID using:

    resolved IID = values[2 + zoom slot]

RKT3 has been used for true 3D network models where separate geometry is desirable at each zoom.

## RKT4

RKT4 supports:

- Multiple models in one state
- Separate model states
- Overhanging models
- Per-model X, Y and Z offsets
- Invisible states
- Timed, day/night and seasonal props

Each model is represented by an eight-value record:

    Rep 1: State
    Rep 2: X offset
    Rep 3: Y offset (vertical)
    Rep 4: Z offset
    Rep 5: Inner Resource Key Type
    Rep 6: Model Type ID
    Rep 7: Model Group ID
    Rep 8: Model Instance ID

The record can be repeated to add further models or states:

    State,X,Y,Z,RKT,TID,GID,IID,
    State,X,Y,Z,RKT,TID,GID,IID,
    ...

### State

The first value identifies the model state:

    0 = normal state
    1 = special state

The game displays every record whose state value matches the state requested for the prop. If a state has no matching records, the prop is invisible in that state.

The special state may be controlled by properties including:

- Nighttime State Change
- Prop Time of Day
- Simulator Date Start
- Simulator Date Duration
- Simulator Date Interval

A null TGI can also be used as an explicitly invisible model:

    0x00000000,0x00000000,0x00000000

Although normal timed props use states 0 and 1, the model-selection routine compares the requested state to the stored value rather than treating it as a Boolean.

### Offsets

The X, Y and Z offsets are signed 16.16 fixed-point values. Divide the signed 32-bit value by `0x10000` (65536) to obtain metres:

    metres = signed raw value / 65536

Examples:

| Raw value    | Offset     |
|--------------|------------|
| `0x00010000` | 1 metre    |
| `0x00008000` | 0.5 metres |
| `0xFFFF0000` | -1 metre   |

Y is the vertical axis.

### Inner Resource Key Type

The commonly supported inner types are:

| Value        | Meaning |
|--------------|---------|
| `0x27812820` | RKT0    |
| `0x27812821` | RKT1    |

These determine whether the referenced TGI represents one model for all views or an inferred RKT1 model family.

The executable also contains handling branches for RKT2 and RKT3 identifiers inside RKT4 data, but their record lengths do not agree cleanly with the standalone property layouts. No standard use is known. RKT0 and RKT1 should be used unless a tested implementation demonstrates otherwise.

### Examples

One RKT1 model in the normal state, with no offset:

    0x00000000,
    0x00000000,0x00000000,0x00000000,
    0x27812821,
    0x5AD0E817,0xBADB57F1,0x12340000

The same model shifted 1 metre in X and 0.5 metres vertically:

    0x00000000,
    0x00010000,0x00008000,0x00000000,
    0x27812821,
    0x5AD0E817,0xBADB57F1,0x12340000

Two models in the same state are created by placing two records with the same state value.

A simple daytime-only prop may use an invisible normal state and a visible special state:

    0x00000000,
    0x00000000,0x00000000,0x00000000,
    0x27812821,
    0x00000000,0x00000000,0x00000000,

    0x00000001,
    0x00000000,0x00000000,0x00000000,
    0x27812821,
    0x5AD0E817,0xBADB57F1,0x12340000

A Prop Time of Day value of `6,20` would make the special state active from 06:00 to 20:00.

## RKT5

RKT5 references an inferred model family containing separate models for zoom, rotation and state. It stores one base TGI:

    Rep 1: Type ID
    Rep 2: Group ID
    Rep 3: Base Instance ID

The game resolves the model IID using:

    resolved IID =
        base IID
        + state × 0x10000
        + zoom slot × 0x100
        + rotation slot × 0x10

For a base IID of `0x16900000`:

    State 0 begins at 0x16900000
    State 1 begins at 0x16910000
    State 2 begins at 0x16920000

Each state normally contains 20 models:

    5 zooms × 4 rotations

RKT5 does not store a state count. The system using the model supplies the requested state, and the corresponding IID is derived from the base key.

Maxis uses RKT5 for several flora exemplars. Most of these contain three model states. One deciduous flora family contains nine populated state indices:

    0, 1, 2, 3, 6, 7, 8, 9, A

This demonstrates that RKT5 state indices may be sparse and are not restricted to states 0 and 1.

## Mirrored resource keys

The mirrored resource-key properties use IDs `0x100` above the corresponding primary property:

| Primary      | Mirrored     | Common name |
|--------------|--------------|-------------|
| `0x27812820` | `0x27812920` | RKTMisc     |
| `0x27812821` | `0x27812921` | RKT1xm      |
| `0x27812822` | `0x27812922` | RKT2xm      |
| `0x27812823` | `0x27812923` | RKT3xm      |
| `0x27812824` | `0x27812924` | RKT4xm      |
| `0x27812825` | `0x27812925` | RKT5xm      |

They use the same stored layouts and resolution rules as their primary counterparts. Mirrored properties are used where the game requires an alternate model family for a mirrored orientation, notably in some Type 21 and network-related exemplars.

## Editing considerations

Changing the RKT property of an existing prop changes the model used by every lot that references that prop exemplar. When creating a new timed, seasonal or replacement prop, a new exemplar with a unique Group and Instance ID should normally be created instead of overriding a widely used prop. Otherwise also Prop Pox has been known to occur

When converting RKT4 back to a simpler format, note that RKT0, RKT1 and RKT3 cannot preserve multiple states, multiple component models or offsets. Such conversions may be lossy.

RKT values should also be checked for:

- Missing referenced models
- Incomplete zoom or rotation sets
- More than one primary RKT property
- Invalid RKT4 record lengths
- Unsupported RKT4 inner types
- Missing RKT5 state resources
