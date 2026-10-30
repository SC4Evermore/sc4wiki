---
title: "Lot Subfile"
description: ""
published: false
date: '2019-08-10T01:24:09Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:24:09Z'
---

This page pertains to the format of the **Lot Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *C9BD5D4A*. It can be viewed and mapped using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Description

This subfile contains data about all the [lots](/lot) in the city. Used for both ploppable and growable lots.

## Structure

The Lot Subfile has the following format:

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version?  (only seen 0x0008)
    DWORD   Lot IID
    BYTE    Flag byte 1  (See Appendix 1 below)
    BYTE    Min X Tile
    BYTE    Min Z Tile
    BYTE    Max X Tile
    BYTE    Max Z Tile
    BYTE    Commute X Tile
    BYTE    Commute Z Tile
    FLOAT32 Y Position
    FLOAT32 Y Coordinate if slope conforming, height above Y Position (0x00000000 if Lot Foundation)
    FLOAT32 Y Coordinate if slope conforming, height above Y Position (0x00000000 if Lot Foundation)
    BYTE    Lot Width
    BYTE    Lot Depth
    BYTE    Lot Orientation
    BYTE    Flag byte 2  (See Appendix 2 below)
    BYTE    Flag byte 3  (See Appendix 3 below)
    BYTE    Zone Type
    BYTE    Zone Wealth
    DWORD   Date Lot Appeared (was plopped or grew)
    DWORD   Building IID
    BYTE    Unknown, several values seen, but the same value often appears in several lots
    DWORD   Memory Address for linked industrial lot
        DWORD   0x4A232DA8, Industry Subfile Type ID. Appears only if the previous DWORD is not 0x00000000
    DWORD   Memory Address of the Anchor or Farm Lot
        DWORD   0xC9BD5D4A, Lot Subfile Type ID. Appears only if the previous DWORD is not 0x00000000
    BYTE    Count  (0x00 or 0x01)
        BYTE    Count of RCI Types  (0x01, 0x02 or 0x03)
            DWORD   Demand Source Index  (See Appendix 4 below)
            WORD    Capacity
    BYTE    Count of RCI Types  (0x00, 0x01, 0x02 or 0x03)
        DWORD   Demand Source Index  (See Appendix 4 below)
        WORD    Total Capacity  (including filler lots, e.g. farm fields, mechanics and outs)
    FLOAT32 Total § Capacity  (for C, I and Civics, 0x00000000 for R) - see also SGPROP 0x8A0B4100
    FLOAT32 Total §§ Capacity  (for C, I and Civics, 0x00000000 for R) - see also SGPROP 0x8A0B4100
    FLOAT32 Total §§§ Capacity  (for C, I and Civics, 0x00000000 for R) - see also SGPROP 0x8A0B4100
    WORD    0x0002  (Unknown)
    DWORD   Count of Properties  (I've seen up to 0x00000007)
        SGPROP  SaveGame Properties, repeated Count times  (See Appendix 5 below)
    DWORD   Count of Commute Blocks  (number of destinations commuted to from here)
        DWORD   Count of Commute Paths  (usually 0x00000002 = morning and evening)
            DWORD   Count of Bytes in the Path
            BYTES   Commute Path  (See Appendix 6 below)
        DWORD   Number of Commuters
        BYTE    Unknown, 0x00 or 0x03
        BYTE    Unknown, 0x00, 0x01 or 0x02
        BYTE    Unknown, 0x08, 0x09, 0x0A or 0x0B  (0x00 if the commute path has disappeared)
        BYTE    Unknown, 0x00 or 0x03  (0x04 if the commute path has disappeared)
        SINT16  Commute Destination, X Tile  (See Appendix 7 below)
        SINT16  Commute Destination, Z Tile  (See Appendix 7 below)
        FLOAT32 Trip Length
        DWORD   Unknown  (See Appendix 8 below)
    BYTE    Unknown (takes many different values)

### Appendix 1 - Flag Byte 1

        0x01 (00000001b) - Might have to do with road access
        0x02 (00000010b) - Might have to do with road (job?) access
        0x04 (00000100b) - Might have to do with road access
        0x08 (00001000b) - Means the lot is watered
        0x10 (00010000b) - Means the lot is powered
        0x20 (00100000b) - Means the lot is marked historical
        0x40 (01000000b) - Might mean the lot is built

### Appendix 2 - Flag Byte 2

This one is normally *0x03*, but *0x00, 0x01, 0x02, 0x04 and 0x06* have also been seen. It seems to be going hand-in-hand with Flag Byte 1:

        0x01 (00000001b) - Flag Byte 1 = 0x10 - Powered (empty growable zones)
        0x02 (00000010b) - Flag Byte 1 = 0x50 - Powered and built
        0x03 (00000011b) - Flag Byte 1 = 0x58 - Powered, watered and built
        0x04 (00000100b) - Seen it once on a tall office under construction
        0x06 (00000110b) - Seen it once on a water tower without power

### Appendix 3 - Flag Byte 3

This is normally *0x00*, but *0x01, 0x03 and 0x06* have also been seen. All those having 0x01 or 0x03 were growable lots under construction. Thus, the lowest bit seems obvious after a number of confirmations:

        0x01 (00000001b) - A growable lot that is under construction
        0x02 (00000010b) - ?
        0x04 (00000100b) - ?

### Appendix 4 - Demand Source Index

        0x00001010 = R§
        0x00001020 = R§§
        0x00001030 = R§§§
        0x00003110 = CS§
        0x00003120 = CS§§
        0x00003130 = CS§§§
        0x00003320 = CO§§
        0x00003330 = CO§§§
        0x00004100 = IR
        0x00004200 = ID
        0x00004300 = IM
        0x00004400 = IHT

### Appendix 5 - Structure of SGPROP (SaveGame Properties)

This structure is used on the SGPROP entries. Known entries are listed further below.

    DWORD   Property Name Value
    DWORD   Property Name Value  (doubled for some unknown reason)
    DWORD   0x00000000
    BYTE    Data Type, 01=UInt8, 02=UInt16, 03=UInt32, 07=SInt32, 08=SInt64, 09=Float32, 0B=Boolean
    BYTE    KeyType, 0x00 = 0 reps, 0x80 = more than 0 reps
    WORD    0x0000
    DWORD   Rep Count  (this one appears only if KeyType = 0x80)
    DATA    Property Value (repeated Rep Count times, type according to Data Type)

### Appendix 6 - Structure of Commute Paths

    BYTE    Starting Traffic Type  (see below)
    BYTE    Path Start Tile X (network in front of the lot)
    BYTE    Path Start Tile Z (network in front of the lot)

      Commute legs, repeated for each transit switch
        BYTE    Transit Switch 0x4T  (T = Traffic type, see below)
        BYTE    Length of Path (Count of quads)
            TAYSTE      Path Direction  (0 = West, 1 = North, 2 = East, 3=South)
        TAYSTES 00b  (repeated 0, 1, 2 or 3 times, in order to fill the last BYTE)

Traffic types are in the same order as in the [Traffic Simulator](/traffic-simulator):

        0x00 = Walk
        0x01 = Car
        0x02 = Bus
        0x03 = Passenger Train
        0x04 = Freight Truck
        0x05 = Freight Train
        0x06 = Subway
        0x07 = Light Rail
        0x08 = Monorail

A tayste is two bits, one byte contains four taystes. Each tayste takes the path one tile in the direction indicated.

### Appendix 7 - Destination Tile

A job located in a neighbouring city has the XZ coordinate of the border crossing.

- A job located in the western neighbour has an X coordinate of -1 (0xFFFF).
- A job located in the northern neighbour has a Z coordinate of -1 (0xFFFF).
- A job located in the eastern neighbour has an X coordinate of 64 (0x0040), 128 (0x0080) or 256 (0x0100).
- A job located in the southern neighbour has a Z coordinate of 64 (0x0040), 128 (0x0080) or 256 (0x0100).

If the commute path has disappeared (e.g. work demolished or redeveloping), the X coordinate becomes 0xDFA8 (-8,280).

### Appendix 8 - Unknown

For residential lots, this value is often 2, but values of 9 and 11 have also been observed. This value is always 16 for industrial lots. If the commute path has disappeared (e.g. work demolished or redeveloping), this DWORD becomes *0x0012FC70*.

## Savegame Properties (SGProps)

Known entries for SGPROP for the Lot Subfile are listed below.

    0x2A4F9C74 - Unknown
    Type: UInt32
    Rep Count = 1 (usually, but 6 has been seen for the passenger rail station)

    0x4A611773 - Unknown
    Type: UInt8 (Type 01)
    Rep Count = 0

    0x691C863C - Unknown
    Type: UInt32
    Rep Count = 0

    0x8999B10B - Unknown
    Type: UInt32
    Rep Count = 0

    0x8999B20B - Unknown
    Type: UInt32
    Rep Count = 0

    0x8A0B4100 - Job/Freight Capacity and Usage (for C, I and Civics)
    Type: UInt16 (Type 02)
    Rep Count = 12
    Rep 1 = Integer Value of Total § Capacity
    Rep 2 = Integer Value of Total §§ Capacity
    Rep 3 = Integer Value of Total §§§ Capacity
    Rep 4 = Freight Capacity (only for ports)
    Rep 5 = Some § Job Count
    Rep 6 = Some §§ Job Count
    Rep 7 = Some §§§ Job Count
    Rep 8 = Some Freight Usage (only for ports)
    Rep 9 = Actual § Job Count
    Rep 10 = Actual §§ Job Count
    Rep 11 = Actual §§§ Job Count
    Rep 12 = Actual Freight Usage (only for ports)

    0xC999C45E - Unknown
    Type: UInt32
    Rep Count = 0

    0xC999E206 - Unknown
    Type: UInt32
    Rep Count = 0

    0xE999B11F - Unknown
    Type: UInt32
    Rep Count = 0

    0xEA54D283 - Budget Item: Department
    Type: UInt32
    Rep Count = 1 (0xC921CEEB = Mass Transit)

    0xEA54D284 - Budget Item: Line
    Type: UInt32
    Rep Count = 1 (0x00000001)

    0xEA54D285 - Budget Item: Purpose
    Type: UInt32
    Rep Count = 1 (0xCA550301 = Mass Transit Switch)

    0xEA54D286 - Budget Item: Cost
    Type: SInt64
    Rep Count = 1 (0x000000000000000A = 10 § per month)
