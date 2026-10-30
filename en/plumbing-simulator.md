---
title: "Plumbing Simulator"
description: ""
published: false
date: '2021-07-06T12:06:04Z'
tags: []
editor: markdown
dateCreated: '2021-07-06T10:04:39Z'
---

This page pertains to the format of the **Plumbing Simulator** Subfile within [Savegame](/savegame) files. This file has Type ID **0x298f9b2d**. This particular subfile was decoded by .

The plumbing simulator contains a few lists:

- A 2-dimensional array containing a byte for every tile in the city (values not studied in detail yet).
- A list of pointers to all water producing buildings (note: pointers are always stored as two consecutive DWORDS containing address and Type ID).
- A list of pointers to all pipe segments from the [Pipe Occupant Subfile](/pipe-occupant-subfile).

## Structure

    DWORD   Size
    DWORD   CRC
    DWORD   Memory address
    DWORD   Major version (0x0004)
    DWORD   Pointer to SimGrid
    DWORD   0x49b9e602 (Type ID of SimGridUint8)
    DWORD   Pointer to SimGrid
    DWORD   0x49b9e602 (Type ID of SimGridUint8)
    DWORD   xSize of city (64, 128 or 256)
    DWORD   zSize of city (64, 128 or 256)
        BYTE    A byte for every tile in the city. Order is (0, 0), (1, 0), ...
    DWORD   Revision. Seems like every time you change something to the plumbing situation
        (such as building a water tower, laying pipes, ...) this value is increased by 1.
    DWORD   Unknown (mostly 0x00000000, seen 24 and 42 as well).
    DWORD x 2   Unknown (only seen 0x00000000)
    DWORD   Number of water related buildings
    DWORD   Unknown (only seen 0x00000000)

        # Repeat for amount of buildings
        DWORD   X coordinate of anchor building
        DWORD   Z coordinate of anchor building
        DWORD   Min X coordinate of lot
        DWORD   Min Z coordinate of lot
        DWORD   Max X coordinate of lot
        DWORD   Max Z coordinate of lot
        DWORD   Water produced per month
        DWORD   Actual water produced per month (uses degradation)
        DWORD   Pointer to entry in building subfile
        DWORD   0xa9bd882d (Type ID of building subfile)

    DWORD x 9   Unknown (only seen 0x00000000)
    BYTE    Unknown (only seen 0x02)
    DWORD   Unknown (only seen 0x00000000)
    DWORD   City size (64, 128 or 256)
    DWORD x 3   Unknown (only seen 0x00000000)
    DWORD   X size of city minus 1 (63, 127 or 255)
    DWORD   Z size of city minus 1 (63, 127 or 255)
    DWORD   Water filter capacity?
    DWORD   Unknown (only seen 0x00000000)
    DWORD   Amount of pipe segments to follow
    DWORD x 2 (Unknown, only  seen 0x00000000)
        
        # Repeat for amount of pipe sections
        DWORD   Pointer to Pipe Occupant record
        DWORD   0x49c05b9f (Type ID of PipeOccupant)

    DWORD   Pointer to Department Budget record
    DWORD   0xe990bffc (Type Id of Department Budget)
    DWORD   Total water produced
    DWORD   Unknown (only seen 0x00000000)
    DWORD   Actual filter capacity, taking into account degradation?
    DWORD x 5   Unknown (only seen 0x00000000)
