---
title: "SimGrid"
description: ""
published: true
date: '2020-03-18T11:21:09Z'
tags: []
editor: markdown
dateCreated: '2020-03-18T11:20:35Z'
---

**SimGrids** are files that can be found within [Savegame](/savegame) files. They come in 6 different types:

| Type ID    | Name           |
|------------|----------------|
| 0x49b9e602 | SimGridUint8   |
| 0x49b9e603 | SimGridSint8   |
| 0x49b9e604 | SimGridUint16  |
| 0x49b9e605 | SimGridSint16  |
| 0x49b9e606 | SimGridUint32  |
| 0x49b9e60a | SimGridFloat32 |

They are basically rectangular grids that hold values that the game needs for the simulation. Most of them can be viewed in the Mayor Mode Data Views.

This particular subfile was decoded by .

## Structure

    DWORD   Subfile Size in bytes
    DWORD   CRC
    DWORD   Memory address
    WORD    Major version (0x0001)
    BYTE    Unknown
    DWORD   Type ID (0x49b9e602 to 0x49b9e60a)
    DWORD   Data ID
    DWORD   Resolution
    DWORD   Resolution power
    DWORD   X size
    DWORD   Z size
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown
        TYPE    Values (repeat for x*z times, byte size depends on Type ID)

### Data ID

The Data ID specifies what kind of data this SimGrid holds. Not all Data IDs are know yet.

| Data ID | Data type | Name | Description |
|----|----|----|----|
| 0x41800000 | Sint8 | City Overview | The values in it correspond ZoneTypes from the [Lot Subfile](/lot-subfile) |
| 0x69d5c40e | Float32 |  | Traffic related, probably all traffic |
| 0x69d5c3ac | Float32 |  | Traffic related, probably car traffic |
| 0x49d5bc40 | Int16 | Air pollution |  |

### Resolution and resolution power

The SimGrids don't always hold values per tile. If the values are set per 1x1, resolution is 1, if values are set per 2x2, resolution is 2 etc. This value is always a power of 2 (so 1x1, 2x2, 4x4, ...) The exponent is given by the resolution power.

### X size & Z size

The amount of rows and columns in the grid. For a small 64x64 city and resolution 1, X & Z size are 64. When the resolution is 2, X & Z size are 32 and so on.

### Values

The values for each cell of the grid. The byte size of each value depends on the type of the SimGrid. For Uint8's, this is 1 byte, for Float32's this is 4 bytes and so on.

The order of values is **column first**. So first comes (0,0), then (0,1), then (0, 2) and so on.
