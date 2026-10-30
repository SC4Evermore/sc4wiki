---
title: "Industry Subfile"
description: ""
published: true
date: '2019-08-10T02:38:02Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T02:38:02Z'
---

This page pertains to the format of the **Industry Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *4A232DA8*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Structure

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version  (only seen 0x0001)
    DWORD   Count  (number of industrial lots linked through the first one, which is the anchor or farm)
       DWORD        Link: Memory address
       DWORD    Link: Subfile Type ID (always 0xC9BD5D4A - Lot Subfile)
