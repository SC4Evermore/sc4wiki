---
title: "Prop Subfile"
description: ""
published: true
date: '2019-08-10T02:39:11Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T02:39:11Z'
---

This page pertains to the format of the **Prop Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *2977AA47*. It can be viewed and mapped using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Structure

The Prop Subfile has the following format:

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version?  (only seen 0x0006)
    WORD    Minor Version?  (only seen 0x0004)
    WORD    Zot  (almost always 0x0000, however 0x0101 for a zot)  (See Appendix 5 below)
    BYTE    Unknown  (only seen 0x00)
    BYTE    Appearance Flag  (See Appendix 2 below)
    DWORD   0xA823821E  (always the same)
    BYTE    Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD    X Tract Size? (power of 2)  (only seen 0x0002)
    WORD    Z Tract Size? (power of 2)  (only seen 0x0002)
    DWORD   Count of Properties  (I've seen 0x00000000, 0x00000001 and 0x00000003)
        SGPROP      SaveGame Properties, repeated Count times  (See Appendix 1 below)
    DWORD   Group ID  (from the Prop Exemplar)
    DWORD   Type ID  (from the Prop Exemplar)
    DWORD   Instance ID  (from the Prop Exemplar)
    DWORD   Instance ID  (the value given when the prop appeared)
    FLOAT32 Min X Coordinate
    FLOAT32 Min Y Coordinate
    FLOAT32 Min Z Coordinate
    FLOAT32 Max X Coordinate
    FLOAT32 Max Y Coordinate
    FLOAT32 Max Z Coordinate
    BYTE    Orientation
    BYTE    State
    BYTE    Start Time (in 0.1 hours)
    BYTE    Stop Time (in 0.1 hours)
    BYTE    Count  (0 or 1)
        DWORD   Interval (in days)
        DWORD   Duration (in days)
        DWORD   Start Date (in Julian days)
        DWORD   End Date (in Julian days)
    BYTE    Random Chance of Appearance (0-100)
    BYTE    Lot Type  (See Appendix 3 below)
    DWORD   Object ID
    BYTE    Conditional Appearance  (See Appendix 4 below)

### Appendix 1 - Structure of SGPROP (SaveGame Properties)

This structure is used on the SGPROP entries. Known entries are listed further below.

    DWORD   Property Name Value
    DWORD   Property Name Value  (doubled for some unknown reason)
    DWORD   0x00000000
    BYTE    Data Type, 01=UInt8, 02=UInt16, 03=UInt32, 07=SInt32, 08=SInt64, 09=Float32, 0B=Boolean
    BYTE    KeyType, 0x00 = 0 reps, 0x80 = more than 0 reps
    WORD    0x0000
    DWORD   Rep Count  (this one appears only if KeyType = 0x80)
        DATA    Property Value (repeated Rep Count times, type according to Data Type)

### Appendix 2 - Appearance Flag (offset 0x0013)

The Appearance Flag can have any of the following values:

- 0x01 (00000001b) - Prop that appears in the game (if this is off, the prop has been deleted).
- 0x02 (00000010b) - ? (unused).
- 0x04 (00000100b) - ? (always on).
- 0x08 (00001000b) - Flora (every entry in the flora subfile has 0x0D).
- 0x10 (00010000b) - Fauna (every entry in the fauna subfile has this bit set).
- 0x40 (01000000b) - The prop is burnt.
- 0x80 (10000000b) - Disabled [ATC](/atc) or Timed Prop (no animation).

### Appendix 3 - Lot Type

Occurs at offset *0x0052 + Size of SGPROPs*.

Only one of these can be set concurrently. Note, props with Lot Type = 0x01 get an Object ID of *0xFFFFFFFF*. Zots also get an Object ID of *0xFFFFFFFF*, but the Lot Type is 0x02.

- 0x00 (00000000b) - Prop that does not belong in the game (deleted).
- 0x01 (00000001b) - Prop that does not belong to any lot (e.g. border connections).
- 0x02 (00000010b) - Prop that belongs to a normal lot.
- 0x04 (00000100b) - Prop that belongs to a [Type21](/type21) lot.

### Appendix 4 - Conditional Appearance (offset 0x0010)

Normally 0x00. Takes different values for props made conditional in different ways:

- 0x00 - Any non-conditional prop in any state.
- 0x05 - Requires Power to Appear and Date Timed prop, in state 1.
- 0x06 - Requires Power to Appear and Hour Timed prop, in state 1.
- 0x07 - Requires Power to Appear, in state 1.
- 0x0B - ? (Seen once in Riquelandia for effect *0xEA8DE9EB* in state 1).
- 0x0D - Date Timed prop, in state 1.
- 0x0E - Hour Timed prop, in state 1.
- 0x0F - Timed prop in state 0, or any prop with Chance \< 100% in any state.

More testing needed here!

### Appendix 5

For zots, the type is given in SGPROP 0x48E95539:

        0x00000004 = No Power Zot
        0x00000005 = No Water Zot
        0x00000006 = No Road Zot
        0x00000007 = No Work Zot

## Savegame Properties (SGProps)

Known entries for SGPROP for the Prop Subfile are listed below.

### 0x48E95539 - Zot Type

    Data Type: UInt32
    Rep Count: 0

        0x00000004 = No Power Zot
        0x00000005 = No Water Zot
        0x00000006 = No Road Zot
        0x00000007 = No Work Zot

### 0x69DBEBE1 - Unknown

    Data Type: Boolean
    Rep Count: 0
    Values seen: always False (never True)
    This is rare, but has been found in the prop subfile, the flora subfile and the building subfile.

### 0x89A1C16C - Unknown

    Data Type: UInt32
    Rep Count: 0
    This is by far the most common SGPROP in props.
    Values seen: 0, but there has once been seen a 1 (in Baza, for a car having a Requester Satisfaction of Crime).

### 0xCAA45670 - Unknown - Neighbour Connection?

    Data Type: UInt32
    Rep Count: 0
    Values seen: 1 (and nothing else)
    This property always appears together with 0xCAA46595 and either 0xCAA45671 or 0xCAA45672.

### 0xCAA45671 - Unknown - Neighbour Power Connection?

    Data Type: UInt32
    Rep Count: 0
    Values seen: 1 (and nothing else)
    This property always appears together with 0xCAA45670 and 0xCAA46595.

### 0xCAA45672 - Unknown - Neighbour Water Connection?

    Data Type: UInt32
    Rep Count: 0
    Values seen: 1 (and nothing else)
    This property always appears together with 0xCAA45670 and 0xCAA46595.
    I have never seen both 0xCAA45671 and 0xCAA45672 in the same city.

### 0xCAA46595 - Unknown - Neighbour Road Connection?

    Data Type: UInt32
    Rep Count: 0
    Values seen: 1 (and nothing else)
    This property mostly appears together with 0xCAA45670 and either 0xCAA45671 or 0xCAA45672.
    It has been seen on its own as well though.
