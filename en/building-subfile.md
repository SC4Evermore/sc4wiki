---
title: "Building Subfile"
description: ""
published: true
date: '2019-08-05T02:23:11Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2012-09-16T02:37:59Z'
---

This page pertains to the format of the **Building Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *A9BD882D*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Description

This subfile contains data about all of the buildings in the city.

## Structure

The structure of the Building Subfile follows the format below. Somebody should clarify which part of this repeats for each building.

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version?  (only seen 0x0002)
    WORD    Minor Version?  (only seen 0x0004)
    WORD    Zot Word  (always 0x0000 for buildings)
    BYTE    Unknown  (only seen 0x00)
    BYTE    Appearance Flag  (see Appendix 2 below)
    DWORD   0x278128A0  (always the same)
    BYTE    Min Tract X Coordinate
    BYTE    Min Tract Z Coordinate
    BYTE    Max Tract X Coordinate
    BYTE    Max Tract Z Coordinate
    WORD    X Tract Size? (power of 2)  (only seen 0x0002)
    WORD    Z Tract Size? (power of 2)  (only seen 0x0002)
    DWORD   Count of Properties  (can be several of them)
        SGPROP      SaveGame Properties, repeated Count times  (see Appendix 1 below)
    BYTE    Unknown  (only seen 0x01)
    DWORD   Group ID  (from the Prop Exemplar)
    DWORD   Type ID  (from the Prop Exemplar)
    DWORD   Instance ID  (from the Prop Exemplar)
    DWORD   Instance ID  (the value given when the building appeared)
    FLOAT32 Min X Coordinate
    FLOAT32 Min Y Coordinate
    FLOAT32 Min Z Coordinate
    FLOAT32 Max X Coordinate
    FLOAT32 Max Y Coordinate
    FLOAT32 Max Z Coordinate
    BYTE    Orientation
    FLOAT32 Scaffolding Height (see Appendix 3 below)

### Appendix 1: Structure of SGPROP (SaveGame Properties)

This structure is used on the SGPROP entries. Known entries are listed further below.

    DWORD   Property Name Value
    DWORD   Property Name Value (doubled for some unknown reason)
    DWORD   0x00000000
    BYTE    Data Type: 01=UInt8, 02=UInt16, 03=UInt32, 07=SInt32, 08=SInt64, 09=Float32, 0B=Boolean, 0C=String
    BYTE    KeyType: 0x00 = 0 reps, 0x80 = more than 0 reps
    WORD    0x0000
    DWORD   Rep Count  (this one appears only if KeyType = 0x80)
        DATA    Property Value (repeated Rep Count times, type according to Data Type)

### Appendix 2: Appearance Flag (offset 0x0013)

The Appearance Flag can have any of the following values:

- 0x01 (00000001b) - Building that appears in the game (if this is off, the building has been deleted).
- 0x02 (00000010b) - ? (unused).
- 0x04 (00000100b) - ? (always on).
- 0x08 (00001000b) - Flora (not used for buildings).
- 0x40 (01000000b) - Burnt (probably not used for buildings, as if they burn, they become replaced by a burnt prop).

### Appendix 3: Scaffolding Height

Depending on the height of the finished building, the scaffolding height is divided into a number of (let's call it F) fractions. During construction, if the building is growable (or LotConfigPropertyDoConstruction = True), the scaffolding will jump up in steps equal to 1/F of the final height.

The height of the current scaffolding is given in this field. Checking several buildings under construction of different heights, the following values have been found:

    1/2,  1/3,  2/3,  3/5,  4/5,  2/7,  4/7,  4/9,  8/17,  7/20

Once the scaffolding enters the height of the final building, this field will get a value of 1.00. A finished building always has a value of 1.00 in this field.

## Savegame Properties (SGProps)

Known entries for SGPROP for the Building Subfile are listed below.

    0x899AFBAD - Custom Name
    Type: String
    Rep Count = String Length
    Contains the customized name given to a building in the game

    0x08D9763D - Utility Usage
    Type: UInt32/SInt32
    Rep Count = 0
    UInt32 for Water Pumps
    SInt32 for Power Plants
    0x00000000 for newly plopped facilities
    The actual amount of water and power produced (and used by the city).

    0x2A58D350 - Actual Monthly Cost at full funding
    Type: SInt64
    Rep Count = 0
    Only for utility buildings, not for other civic buildings.
    Takes into account "Funding percentage to decay rate multiplier response curve".

    0xEA54D284 - Budget Panel Identification
    Type: UInt32
    Rep Count > 0
    Normally a link to the Building Exemplar's IID
    0x00000001 = Ambulance or School Bus

    0xEA54D287 - Local Budget Funding in %
    Type: Float32
    Rep Count > 0
    Funding percentage of those items set in 0xEA54D284

    0x0910BFCF - Accumulated Age Degradation
    Type: Float32
    Rep Count = 0

    0xE9244B2E - School Capacity (actual capacity, based on funding)
    Type: UInt32
    Rep Count = 0

    0x09220161 - School Usage (actual number of students)
    Type: UInt32
    Rep Count = 0
    0xFFFFFFFF if newly plopped

    0x49244B21 - Hospital Capacity (actual capacity, based on funding)
    Type: UInt32
    Rep Count = 0

    0xC922015C - Hospital Usage (actual number of patients)
    Type: UInt32
    Rep Count = 0
    0xFFFFFFFF if newly plopped

    0x292453C5 - School Grade? (between 0.00 and 1.00)
    0x2A976C20 - School Grade? (between 0.00 and 1.00)
    Type: Float32
    Rep Count = 0
    One is probably the grade. What is the other one?

    0x092453CB - Hospital Grade? (between 0.00 and 1.00)
    0xAA976BE7 - Hospital Grade? (between 0.00 and 1.00)
    Type: Float32
    Rep Count = 0
    One is probably the grade. What is the other one?

    0x48D71EE1 - Jail Usage (actual number of inmates)
    Type: UInt32
    Rep Count = 0
    0x00000000 if newly plopped
    For the Modd Squad Safety I had an inmate count of 19 in the query, but this property showed 20.

    0x48D71ED7 - Police Station available(?) dispatches
    Type: UInt32
    Rep Count = 0
    For some reason this is usually not accurate though, compared to the building property Police Station, Total Dispatches, e.g:

     Station    
     Total
        
     SGPROP
     plopped:   
     Dispatches
        
     Dispatches
     Police Kiosk   
     0
        
     1
     Small Police Station   
     2
        
     1
     Large Police Station   
     4
        
     3
     DeLuxe Police Station  
     6
        
     7
     Modd Squad Safety  
     20
        
     21

    Thus, I cannot guarantee what this property is showing.
    However the values are the only ones that even somewhat match up to the total dispatches.

    0x69B425DD - Fire Station available(?) dispatches
    Type: UInt32
    Rep Count = 0
    For some reason this is usually not accurate though, compared to the building property Fire Station, Total Dispatches, e.g:

     Station    
     Total
        
     SGPROP
     plopped:   
     Dispatches
        
     Dispatches
     Small Fire Station 
     1
        
     1
     Large Fire Station 
     2
        
     2
     Fire Landing Strip 
     2
        
     4
     Modd Squad Safety  
     20
        
     21

    Thus, I cannot guarantee what this property is showing.
    However the values are the only ones that even somewhat match up to the total dispatches.

    0x48D71ED8 - Police Station - Unknown property
    Type: UInt32
    Rep Count = 0
    0x00000000 - Police Kiosk
    0x00000003 - Small Police Station
    0x0000000F - Large Police Station
    0x0000003F - DeLuxe Police Station
    0x000FFFFF - Modd Squad Safety

    0x69B425DE - Fire Station - Unknown property
    Type: UInt32
    Rep Count = 0
    0x00000001 - Small Fire Station
    0x00000003 - Large Fire Station
    0x00000003 - Fire Landing Strip
    0x000FFFFF - Modd Squad Safety

    0x8A70A0B9 - Crimes and Arrests
    Type: UInt32
    Rep Count = 4
    Rep 1 = Number of Crimes this month (as reported by the query)
    Rep 2 = Number of Arrests this month (as reported by the query)
    Rep 3 = Number of Crimes the previous month
    Rep 4 = Number of Arrests the previous month

    0xAC0B070E - Unknown - DeLuxe Police Station - Helicopter related?
    Type: UInt32
    Rep Count = 0

    0xEC0B0709 - Unknown - DeLuxe Police Station - Helicopter related?
    Type: UInt32
    Rep Count = 0

    0x0C0AFF3F - Unknown - Fire Landing Strip - Fire Plane related?
    Type: UInt32
    Rep Count = 0

    0xCC0AFDDB - Unknown - Fire Landing Strip - Fire Plane related?
    Type: UInt32
    Rep Count = 0

    0x69DBEBE1 - Unknown
    Data Type: Boolean
    Rep Count: 0
    Values seen: always False (never True)
    This is rare, but has been found in the Prop subfile, the Flora subfile and the Building subfile

NOTE: Just like ordinary police and fire stations, the Modd Squad Safety did not get the property *0xEA54D284* (Budget Panel Identification). Thus, it is not currently known in which order the budget fundings given in *0xEA54D287* are to be read. That property did get three reps, all at 100%, probably for police funding, jail funding and fire station funding.
