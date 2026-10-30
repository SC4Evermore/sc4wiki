---
title: "Tutorial Subfile"
description: ""
published: false
date: '2019-08-10T01:26:37Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:26:37Z'
---

This page pertains to the format of the **Tutorial Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *AA3836FB*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Structure

    DWORD   Size  (always 0x00000017)
    DWORD   CRC
    DWORD   Memory
    WORD    Major Version?  (only seen 0x0002)
    BOOLEAN Tutorial City?  (0x00 = No, 0x01 = Yes)
    DWORD   0x00000000
    DWORD   IID of Tutorial GUID  (if not a tutorial, then 0xFFFFFFFF)
