---
title: "Flora Subfile"
description: ""
published: false
date: '2019-08-10T01:27:04Z'
tags: ["Savegame/Subfiles", "MTS2"]
editor: markdown
dateCreated: '2019-08-10T01:27:04Z'
---

This page pertains to the format of the **Flora Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *A9C05C85*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Description

This subfile contains flora in the city, in a similar way as the [Prop Subfile](/prop-subfile).

## Structure

The Flora Subfile has the following format:

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version?  (only seen 0x0003)
    WORD    Minor Version?  (only seen 0x0004)
    WORD    Zot  (always 0x0000 for flora)
    BYTE    Unknown  (only seen 0x00)
    BYTE    Appearance Flag  (see Appendix 2 below)
    DWORD   0x74758926  (always the same)
    BYTE    Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD    X Tract Size? (power of 2)  (only seen 0x0002)
    WORD    Z Tract Size? (power of 2)  (only seen 0x0002)
    DWORD   Count of Properties  (0x00000000 and 0x00000001 have both been seen here)
        SGPROP      SaveGame Properties, repeated Count times  (see Appendix 1 below)
    DWORD   Group ID  (from the Prop Exemplar)
    DWORD   Type ID  (from the Prop Exemplar)
    DWORD   Instance ID  (from the Prop Exemplar)
    DWORD   Instance ID  (the value given when the flora appeared)
    FLOAT32 X Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Z Coordinate
    DWORD   Date of current growth cycle
    DWORD   Date of first appearance
    BYTE    State
    BYTE    Orientation
    DWORD   Object ID?  (this needs verification)

### Appendix 1: Structure of SGPROP (SaveGame Properties)

This structure is used on the SGPROP entries. Known entries are listed further below.

    DWORD   Property Name Value
    DWORD   Property Name Value  (doubled for some unknown reason)
    DWORD   0x00000000
    BYTE    Data Type, 01=UInt8, 02=UInt16, 03=UInt32, 07=SInt32, 08=SInt64, 09=Float32, 0B=Boolean
    BYTE    KeyType, 0x00 = 0 reps, 0x80 = more than 0 reps
    WORD    0x0000
    DWORD   Rep Count  (this one appears only if KeyType = 0x80)
        DATA    Property Value (repeated Rep Count times, type according to Data Type)

### Appendix 2: Appearance Flag (Offset 0x0013)

The Appearance Flag can have any of the following values:

- 0x01 (00000001b) - Flora that appears in the game (if this is off, the flora has been deleted).
- 0x02 (00000010b) - ? (unused).
- 0x04 (00000100b) - ? (always on).
- 0x08 (00001000b) - Flora (every entry in the flora subfile has 0x0D).
- 0x40 (01000000b) - The flora is burnt.
- 0x80 (10000000b) - Disabled [ATC](/atc) or Timed Prop (no animation).

## Savegame Properties (SGProps)

Known entries for SGPROP for the Flora Subfile are listed below.

    0x69DBEBE1 - Unknown
    Data Type: Boolean
    Rep Count: 0
    Values seen: always False (never True)
    This is rare, but has been found in the Prop subfile, the Flora subfile and the Building subfile
