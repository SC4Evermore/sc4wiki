---
title: "Zone Manager"
description: ""
published: false
date: '2020-03-18T15:21:22Z'
tags: []
editor: markdown
dateCreated: '2020-03-18T15:05:32Z'
---

This page pertains to the format of the **Zone Manager** Subfile within [Savegame](/savegame) files. This file has Type ID **0x298f9b2d**. This particular subfile was decoded by .

## Structure

    DWORD       Size
    DWORD       CRC
    DWORD       Memory address
    WORD        Major version (0x0001)
    DWORD       Pointer to the Zone View SimGrid.
    DWORD       0x49b9e603 (Type ID of cSC4SimGridSint8)
    DWORD x 16  Unknown, probably the amount of lots of each ZoneType
    DWORD x 33  Tiles in the city (0x00001000 for small city, 0x00004000 for medium city, 0x00010000 for large city)
    BYTE x 533  533 unknown bytes, seems to always the same. Small numbers, often 0x00000000
    DWORD       Pointer to cSC4City
    DWORD       0x8990c372 (Type ID of cSC4City)
    DWORD       Pointer to cSC4OccupantManager
    DWORD       0x098f964d (Type ID of cSC4OccupantManager)
    DWORD       Pointer to cSTETerrain
    DWORD       0xe98f9525 (Type ID of cSTETerrain)
    DWORD       Pointer to cSC4PollutionSimulator
    DWORD       0x8990c065 (Type ID of cSC4PollutionSimulator)
    DWORD       Pointer to cSC4BudgetSimulator
    DWORD       0xe990be01 (Type ID of cSC4BudgetSimulator)
