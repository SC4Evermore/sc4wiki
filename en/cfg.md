---
title: "CFG"
description: ""
published: true
date: '2019-08-09T02:54:47Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-04T22:48:52Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**CFG** is the [SimCity 4](/simcity-4) Config format. There is only one file of these files. It is a file contained in "SimCity 4.cfg" in the My Documents SC4 directory. It controls the features of the system. The [TGI](/tgi) for this file is a9dd6e06 49dd6e08 00000001.

It has a simple byte by byte format for the most part. Here's what we know. (Much thanks to [Tropod](/people/tropod) for all this great info):

    1262 Bytes - Unknown
    BYTE  - Auto Edge Reconciliation?
    2575 Bytes - Unknown
    QWORD - Current Region Coordinates
    BYTE  - Show City Boundaries?
    BYTE  - Show City Names?
    BYTE  - Current Region Map View
    BYTE  - Unknown
    BYTE  - Auto Go to Disaster?
    BYTE  - Edge Scrolling?
    BYTE  - Expanded Tooltips?
    BYTE  - Urgent Advice Dialogs?
    BYTE  - Visual Setting Type (0 - User, 1 - Default)
    BYTE  - Visual Effect Quality
    BYTE  - Number of Cars/Sims
    BYTE  - Shadow Quality
    BYTE  - Texture Quality
    BYTE  - Clouds/Fog?
    BYTE  - Waves?
    BYTE  - Render Mode (Software - 0, Hardware - 1)
    BYTE  - Color Cursor?
    BYTE  - UI Transparency?
    BYTE  - City Detail
    BYTE  - Unknown
    BYTE  - Variable Speed Automata?
    BYTE  - Unknown
    BYTE  - Unknown
    BYTE  - Unknown
    DWORD - Game Resolution - Horizontal
    DWORD - Game Resolution - Vertical
    BYTE  - Game Texture Bit Type (16-bit (0x10) or 32-bit (0x20))
    BYTE  - Unknown
    BYTE  - Unknown
    BYTE  - Unknown
    BYTE  - Building Redraw Speed
    2059 Bytes - Unknown
