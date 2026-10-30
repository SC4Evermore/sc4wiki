---
title: "LotConfigPropertyLotObject"
description: ""
published: true
date: '2020-03-14T14:18:29Z'
tags: []
editor: markdown
dateCreated: '2020-03-14T14:18:29Z'
---

This specification is for the **LotConfigPropertyLotObject** property found in Lot Configuration (T10) [Exemplars](/exemplar). This property can be repeated several times within a Lot Exemplar. There must always be at least one of these properties, for the building. There may be several additional LotConfigPropertyLotObject properties in the exemplar as well, as one is required for every physical item (such as a prop or texture) used on the lot.

## Specification

This specification is considered complete as of September 5th, 2004. The LotConfigPropertyLotObject property contains 12-16 reps, defined below, depending on the type of object it is describing. Reps 1-12 have the same definition for all types, while Reps 13-16 (if they exist) have different meanings depending on the type. The type is defined in the first rep of the property.

The following types of LotConfigPropertyLotObject exist:

    0x0: Building: Defines position, and IID reference of building exemplar.
    0x1: Prop: Defines position, and IID reference of a prop exemplar.
    0x2: Texture: Defines position and IID reference of a base or overlay texture.
    0x3: Fence: Not implemented currently.
    0x4: Flora: Defines position, and IID reference of a flora/growable tree exemplar.
    0x5: Water Constraint Tile
    0x6: Land Constraint Tile
    0x7: Network Node: Defines transit connections and automata paths

### Reps 1-12

    Rep #    | Value      | Description
    -----------------------------------------------------------
    1        | 0x0-0x7    | Type descriptor. See above.
    2        | 0xAB       | Level of detail modifier (See Table 3 below)
    3        | 0x0-0x3    | Orientation. 0=South, 1=West, 2=North, 3=East
    4        | *          | X Location Position. 0x00000000-0xFFFFFFFF
    5        | *          | Z Location Position. 0x00000000-0xFFFFFFFF
    6        | *          | Y Location Position. 0x00000000-0xFFFFFFFF
    7        | '''        | X1 Size Position. bounding box
    8        | '''        | Y1 Size Position. bounding box
    9        | '''        | X2 Size Position. bounding box
    10       | '''        | Y2 Size Position. bounding box
    11       | 0x00000000 | Usage (optional/mandatory) Flag. Unused.
    12       | 0xABBBBCCC | ObjectID (See Table 2 below)

    *   These values define position. VERY large numbers.
    ''' These values define bounding box size. VERY large numbers.

The scale of each tile is 0x00100000.

For each location tile, the first three digits are the tile to place on, and the last 5 are the location on the tile. Note that [Reader](/reader) will only identify the first LotConfigPropertyLotObject property in a Lot Exemplar as such, and labels the rest as "Unknown". It also displays all of the reps as hex numbers, as shown in the specification above.

[SC4PIM](/sc4pim) does recognize all instances of this property and displays them as such. It also displays reps 1-10 as decimal numbers, with the following format:

    4        | *          | X Location Position. #/N.NNN
    5        | *          | Z Location Position. #/N.NNN
    6        | *          | Y Location Position. #/N.NNN
    Where # is the number of the tile, and N.NNN is the dimension, in meters, from the edge of that tile.
    Note that tile numbers start at 0.

    7        | '''        | xmin. bounding box
    8        | '''        | ymin. bounding box
    9        | '''        | xmax. bounding box
    10       | '''        | ymax. bounding box
    These are given in meters, from 0.000,0.000 of the lot.

### Reps 13-16

    ---0x0 (Building) Type---
    13       | IID/ID     | For Ploppable buildings, this is the IID of an exemplar/S3D pair.
                  | For Special Buildings (tollbooth, etc.) IID of exemplar for data.
                  | For Growables, the ID of the lots compatible building family.

    ---0x1 (Prop) Type---
    13+      | IID(s)     | Each rep defines sets of one exemplar and one S3D for random props.

    Props may be used to control function. For example, 0x2c520000 through 0x2c54 control Ferry function.
    Applicable GIDs and formats for IIDs for props may be found in the Groups and Instances Format File (InstanceFormats).

    ---0x2 (Texture) Type---
    13       | IID        | Defines an IID of a Texture for a Base or Overlay.

    ---0x3 (Fence) Type---
    NO CUSTOM REPS (Assuming the type worked, this would be an exemplar/S3D pair most probably).

    ---0x4 (Flora) Type---
    13       | IID        | Defines a set of one exemplar and S3D for lot Flora (trees, etc.)

    ---0x5 (Water Constraint) Type---
    NO CUSTOM REPS

    ---0x6 (Land Constraint) Type---
    NO CUSTOM REPS

    ---0x7 (Network Node) Type---
    13       | Type       | Network Connection type (see Table 1 below).
    14       | RUL        | Neighbour Tile Rules (optional and can be left as 00's).
    15       | RUL        | RUL Flags for this tiles connection and which path to use.
    16       | IID        | Custom Sc4path for this tile (optional).

### Table 1 - Network Connection Type

    0x00000000 = Road
    0x00000001 = Rail
    0x00000002 = Highway
    0x00000003 = Street
    0x00000004 = Pipe
    0x00000005 = Power Poles
    0x00000006 = Avenue
    0x00000007 = Subway
    0x00000008 = Elevated Rail
    0x00000009 = Monorail
    0x0000000A = One-way roads
    0x0000000B = ANT (Dirt Roads/RealHighway)
    0x0000000C = Ground Highway

### Table 2 - ObjectID

    0xA0000000 = 0,2,4,6,8,a,c,e - Random one of these characters in case the other ID's are the same.
    0x0BBBB000 = Object Family
    0x00000CCC = Unique Object ID for this family. Incremental for similar objects.

### Table 3 - Level of Detail Modifier

    0x000000A0 = 0,1,2 - Level of detail modifier (0x0 all, 0x10 med and high, 0x20 high only).
    0x0000000B = 0,1 - Prop requester enabled (0x1) or disabled (0x0).

If a prop has the *Requester Satisfaction property* (e.g. wealth or crime) and the requester is enabled, then the prop only appears if this requirement is fulfilled. The level of detail modifier determines which graphics settings are needed for the prop to be displayed.
