---
title: "Lot Developer Subfile"
description: ""
published: true
date: '2021-07-06T10:24:34Z'
tags: []
editor: markdown
dateCreated: '2021-07-06T10:24:34Z'
---

This page pertains to the format of the **Lot Developer** Subfile within [Savegame](/savegame) files. This file has Type ID **0xa990bfe0**. This particular subfile was decoded by .

## Structure

    DWORD   Size
    DWORD   CRC
    DWORD   Memory address
    DWORD   Major version (0x0001)
    DWORD   Tile size of city plus 1 (65, 129 or 257)
    FLOAT32 City width in meters (1024, 2048, 4096)
    FLOAT32 City depth in meters (1024, 2048, 4096)
    DWORD   Amount of building pointers to follow
        DWORD   Pointer to record in Building Subfile
        DWORD   0xa9bd882d (Type ID of Building Subfile)
    DWORD   Unknown (mostly 0x00000000)
    WORD    Unknown (mostly 0x0000)
