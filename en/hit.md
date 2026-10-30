---
title: "HIT"
description: ""
published: false
date: '2019-08-09T02:54:55Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T23:24:56Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

The Maxis **HIT** format was originally from The Sims as a sound companion format.

### Format

`DWORD - HIT! (Identifier)`  
`DWORD - Number of sections in the HIT file`

Index (Repeats sections times):

`DWORD - Section offset`

Section:

`DWORD  - Section ID (TRAX (Track Data))`  
`BYTE[] - Binary Track Data[Entry times]`

`Entry:`  
` DWORD - ENTP (Entry Pointer Section)`  
` --- Repeating ---`  
` DWORD - Track GUID (Instance ID of an AudioScript `[<code>AUS</code>](/aus)` file)`  
` DWORD - Track Offset into TRAX`  
` ------------------`  
` DWORD - EENT (End of Entries)`

### Entries ( A series of instructions and arguments for use on tracks)

    01 - (arg1 as an argument)
    02 - Note On
    05 - Load1 (or v1 as an argument)
    06 - Set (or v2 as an argument)
    07 - (v3 as an argument)
    08 - Return
    09 - Wait
    0B - Wait Samp
    0C - ?End?
    12 - (Patch as an argument)
    18 - Rand
    20 - Loop
    27 - Smart Choose
    3E - Ifeq
    48 - Get SRC Data Field
    55 - TextX
    5F - Smart Index
    ######## - (for load1, the register argument, for ifeq, the index argument)

### Field Definitions from Maxis INI Files

    [RegisterInfo]
    0x00 = arg1,0,0,0xffffffff,"%ld",1
    0x01 = arg2,0,0,0xffffffff,"%ld",1
    0x02 = arg3,0,0,0xffffffff,"%ld",1
    0x03 = arg4,0,0,0xffffffff,"%ld",1
    0x04 = v1,0,0,0xffffffff,"%ld",1
    0x05 = v2,0,0,0xffffffff,"%ld",1
    0x06 = v3,0,0,0xffffffff,"%ld",1
    0x07 = v4,0,0,0xffffffff,"%ld",1
    0x08 = v5,0,0,0xffffffff,"%ld",1
    0x09 = v6,0,0,0xffffffff,"%ld",1
    0x0a = v7,0,0,0xffffffff,"%ld",1
    0x0b = v8,0,0,0xffffffff,"%ld",1
    0x0c = h1,0,0,0xffffffff,"%ld",1
    0x0d = h2,0,0,0xffffffff,"%ld",1
    0x0e = h3,0,0,0xffffffff,"%ld",1
    0x0f = h4,0,0,0xffffffff,"%ld",1
    0x10 = Args Type,0,0,2,"%ld",1
    0x11 = Track Data,0,0,0xffffffff,"<F>",0
    0x12 = Patch,0,0,0xffffffff,"<F>",0
    0x13 = Priority,32,0,127,"%ld",1
    0x14 = Int Vol (db),1024,0,1024,"<db>",10
    0x15 = Ext Vol (db),1024,0,1024,"<db>",10
    0x16 = Pan,512,0,1024,"%ld",100
    0x17 = Pitch,22050,0,100000,"%ld",100
    0x1b = Duck Pri,32,0,127,"%ld",1
    0x25 = Stream,0,0,1,"%ld",1
    0x28 = Fade Var,0,0,255,"%ld",1
    0x30 = Ctrl Group,0,0,0xffffffff,"%ld",1
    0x31 = Self interrupt,0,0,1,"%ld",1
    0x33 = Loop,0,0,1,"%ld",1
    0x36 = Pitch Rand Min,0,-60,60,"%ld",1
    0x37 = Pitch Rand Max,0,-60,60,"%ld",1
    0x3c = Start Delay,0,0,0xffffffff,"%ld",1
    0x3d = Fade In (ms),0,0,0xffffffff,"%ld",1
    0x3e = Fade Out (ms),0,0,0xffffffff,"%ld",1
    0x3f = Hit List,0,0,0xffffffff,"<F>",0
    0x3a = Start Track Var,0,0,0xffffffff,"<F>",0
    0x3b = End Track Var,0,0,0xffffffff,"<F>",0
    24 = kRegIdPaused,0,0,1,"%ld",1
    25 = kRegIdEffectsType,0,0,10,"%ld",1
    26 = kRegIdEffectsLevel,0,0,10,"%ld",1
    28 = kRegId3d,0,0,1,"%ld",1
    29 = kRegIdHeadRelative,0,0,1,"%ld",1
    30 = kRegIdMinDistance,0,0,0xffffffff,"%ld", 10
    31 = kRegIdMaxDistance,0,0,0xffffffff,"%ld", 10
    32 = kRegIdX,0,0,0xffffffff,"%ld", 10
    33 = kRegIdY,0,0,0xffffffff,"%ld", 10
    34 = kRegIdZ,0,0,0xffffffff,"%ld", 10
    35 = kRegIdAttack,0,0,0xffffffff,"%ld",1
    36 = kRegIdDecay    ,0,0,0xffffffff,"%ld",1
    38 = kRegIdBufSizeMultiplier,0,0,10,"%ld",1
    39 = kRegIdFadeDest,0,0,0xffffffff,"%ld",1
    41 = kRegIdFadeSpeed,0,0,0xffffffff,"%ld",1
    42 = kRegIdFadeOn,0,0,1,"%ld",1
    43 = kRegIdPreload,0,0,1,"%ld",1
    44 = kRegIdIsPlaying,0,0,1,"%ld",1
    45 = kRegIdWhatToDoWithUpdate,0,0,0xffffffff,"%ld",0
    46 = kRegIdTempo,0,0,0xffffffff,"%ld",1
    47 = kRegIdTarget,0,0,0xffffffff,"<F>",1
    50 = kRegIdIsPositioned,0,0,1,"%ld",1
    52 = kRegIdAppObjectId,0,0,0xffffffff,"0x%08lx",0
    53 = kRegIdCallbackArg,0,0,0xffffffff,"0x%08lx",1
    56 = kRegIdSpl,0,0,10,"%ld",1
    57 = kRegIdSem,0,0,0xffffffff,"<sem>",0
    60 = kRegIdStartDelay,0,0,10000,"%ld",100
    61 = kRegIdFadeInTime,0,0,10000,"%ld",100
    62 = kRegIdFadeOutTime,0,0,10000,"%ld",100
    63 = kRegIdHitlist,0,0x80000000,0xffffffff,"0x%08lx",0
    64 = kRegIdVelocX,0,0x80000000,0x7fffffff,"%ld",100
    65 = kRegIdVelocY,0,0x80000000,0x7fffffff,"%ld",100
    66 = kRegIdVelocZ,0,0x80000000,0x7fffffff,"%ld",100
    67 = kRegIdOrientX,0,0x80000000,0x7fffffff,"%ld",100
    68 = kRegIdOrientY,0,0x80000000,0x7fffffff,"%ld",100
    69 = kRegIdOrientZ,0,0x80000000,0x7fffffff,"%ld",100
