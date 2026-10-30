---
title: "Zone Developer Subfile"
description: ""
published: false
date: '2021-07-06T11:26:34Z'
tags: []
editor: markdown
dateCreated: '2021-07-06T11:26:21Z'
---

This page pertains to the format of the **Zone Developer** Subfile within [Savegame](/savegame) files. This file has Type ID **0x498f9b01**. This particular subfile was decoded by .

## Structure

    DWORD   Size
    DWORD   CRC
    DWORD   Memory address
    DWORD   Major version (0x0001)
    DWORD   City width in tiles (64, 128 or 256)
    DWORD   City depth in tiles (64, 128 or 256)

        # Repeat for all tiles in the city. Order is column first: (0, 0), (0, 1), ...
        DWORD   Pointer to record in Lot Subfile
        DWORD   0xc9bd5d4a (Type ID of Lot Subfile)
