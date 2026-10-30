---
title: "Region View Subfiles"
description: ""
published: false
date: '2024-12-18T13:40:38Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:23:38Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Region View** file within [Savegame](/savegame) files. The [TGI](/tgi) for this file is *0xCA027EDB, 0xCA027EE1, 0x00000000*.

The Region View file has three possible versions:

- v1.9 - Pre-release
- v1.10 - Release version
- v1.13 - [Rush Hour](/rush-hour)

## Specification

The Region View file has the following specification, written out for version 1.13 type files.

                     
    WORD    Version Major
    WORD    Version Minor
    DWORD   Tile X Location
    DWORD   Tile Y Location
    DWORD   City Size X
    DWORD   City Size Y
    DWORD   Residential Population
    DWORD   Commercial Population
    DWORD   Industrial Population
    FLOAT   Unknown1 (Not Present in version 1.9 or earlier)
    BYTE    Mayor Rating (Bars/12 bars max) (not in version 1.10 or earlier)
    BYTE    Star Count (As seen when looking at a city in region view) (0=1,1=2,2=3)
    BYTE    Tutorial Flag (If 1, map is a tutorial)
    DWORD   City GUID (Present in Mayor View also at offset 20)
                    (Getting Started tutorial has "EXIT".. inside joke?)
    DWORD   Unknown5 (Only seen 0's)
    DWORD   Unknown6 (Only seen 0's)
    DWORD   Unknown7 (Only seen 0's)
    DWORD   Unknown8 (Only seen 0's)
    DWORD   Unknown9 (Only seen 0's)
    BYTE    Mode Flag (1 = Mayor Mode, 0 = God Mode)        
    DWORD   City Name Length
    PRIOR   City Name (String)
    DWORD   Former Name Length
    PRIOR   City Former Name (Non-existent in Region View, Mayor View has "New City")
    DWORD   Mayor Name Length
    PRIOR   Mayor Name (String)
    DWORD   Internal Description Length (Only differs in Mayor View for tutorials)
    PRIOR   Internal Description (String - non-existent in region, name of city/tut in mayor view)
    DWORD   Length
    PRIOR   "Jonas Sparks" (Default mayor?)(Unused)

    -More Zeroes-
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown
    DWORD   Unknown  (Should be 0xFFFFFFFF)

    (Occupant Group Information)
    (There are three sets in all, item listing below.)

    DWORD Occupant Group 1 count (Current Info)
    LOOP
        DWORD Occupant Group
        DWORD Population
    ENDLOOP

    DWORD Occupant Group 2 count (Max Info)
    LOOP
        DWORD Occupant Group
        DWORD Population
    ENDLOOP

    DWORD Occupant Group 3 count (Limits)
    LOOP
        DWORD Occupant Group
        DWORD Population
    ENDLOOP

    DWORD Count (Always 12)
    LOOP
        FLOAT Unknown  (Values are normally the same. Half integer range between 7 and 9.5)
    ENDLOOP

    DWORD Neighbor Connection Count

    LOOP  Neighbor Connection Count
        Begin Neighbor Connection Data

        WORD  Version
        DWORD Network Type
        DWORD Connection X
        DWORD Connection Y
        DWORD Destination Tile X  (FFFF (-1) for places off the region top and left)
        DWORD Destination Tile Y  (Same as above)
        WORD  Unknown             (Usually 512)
        BYTE  Unknown

        DWORD Exemplar property count   (If this is zero, information for the next connection starts.)
            
            ; Below follows a structure that resembles the Exemplar Property structure,
            ; though it is not completely the same. The property ids are apparently unknown
            ; but, I have seen 0x8a0b4100 for example, which is very close to the known
            ; 0x8a0b4103 property, being "FreightReceivingCapacity".
            DWORD Property id
            DWORD Property id repeated (for some reason?)
            DWORD Unknown (0x00000000)
            BYTE  Data Type
            WORD  Key type (0x00 or 0x80)
            BYTE  Unknown

            IF (Key type = 0x00)
                TYPE  Value type depends on data type (0x02 = WORD, 0x03 = DWORD, 0x09 = FLOAT), see exemplar properties
            ELSEIF (Key type = 0x80)
                DWORD  Number of reps to follow
                    TYPE Value type depends on data type (0x02 = WORD, 0x03 = DWORD, 0x09 = FLOAT), see exemplar properties

        ENDLOOP (Exemplar count)
    ENDLOOP (Network connection count)

    DWORD           Unknown count
        DWORD         Unknown
        DWORD         Unknown
        5 BYTES 

    DWORD   Unknown
    FLOAT   Unknown
    DWORD   Unknown
    FLOAT   Unknown

    DWORD   Unknown count
        DWORD   Unknown (Incremental 1-3)
        (following has 5 repeats)
            DWORD       Unknown
            FLOAT       Unknown

    DWORD           Unknown count (76 byte sections)
        WORD          Unknown (5)
        FLOAT         Unknown
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown
        DWORD         Unknown
        DWORD         Unknown (set1.5)
        DWORD         Unknown (set1.5)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set3)
        DWORD         Unknown (set3)
        DWORD         Unknown (set3)
        WORD          Unknown (2)
        DWORD         Unknown
        DWORD         Unknown

    DWORD           Unknown count (76 byte sections)
        WORD          Unknown (5)
        FLOAT         Unknown
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown (set1)
        DWORD         Unknown
        DWORD         Unknown
        DWORD         Unknown (set1.5)
        DWORD         Unknown (set1.5)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set2)
        DWORD         Unknown (set3)
        DWORD         Unknown (set3)
        DWORD         Unknown (set3)
        WORD          Unknown (2)
        DWORD         Unknown
        DWORD         Unknown

    DWORD           Item Count (Typically 0 in unused cities, 2 in used (Version 1.10 and up))
        DWORD         Unknown    (Incremental Value)
        DWORD         Set Count  (Only seen in active cities)
            FLOAT       Unknown
            FLOAT       Unknown
            FLOAT       Unknown

## Occupant Group List

    Max Res Pop
    R$ Max Pop
    R$ Cur Pop
    R$$ Max Pop
    R$$ Cur Pop
    R$$$ Max Pop
    R$$$ Cur Pop
    R$ Jobs
    R$$ Jobs
    R$$$ Jobs
    R$ Workforce EQ1
    R$ Workforce EQ2
    R$ Workforce EQ3
    R$ Workforce EQ4
    R$$ Workforce EQ1
    R$$ Workforce EQ2
    R$$ Workforce EQ3
    R$$ Workforce EQ4
    R$$$ Workforce EQ1
    R$$$ Workforce EQ2
    R$$$ Workforce EQ3
    R$$$ Workforce EQ4
    CS$ Max Jobs
    CS$ Cur Jobs
    CS$$ Max Jobs
    CS$$ Cur Jobs
    CS$$$ Max Jobs
    CS$$$ Cur Jobs
    CO$$ Max Jobs
    CO$$ Cur Jobs
    CO$$$ Max Jobs
    CO$$$ Cur Jobs
    IA Max Jobs
    IA Cur Jobs
    ID Max Jobs
    ID Cur Jobs
    IM Max Jobs
    IM Cur Jobs
    IH Max Jobs
    IH Cur Jobs
