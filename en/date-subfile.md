---
title: "Date Subfile"
description: ""
published: true
date: '2019-08-10T02:38:32Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T02:38:32Z'
---

This page pertains to the format of the **Date Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *2990C1E5*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. Changing the date in here does not work, because it is protected by a checksum. Instead, use the [cheat](/cheat) whattimeizit. This particular subfile was decoded by .

## Structure

    DWORD   Size  (0x0000005B = 91 bytes)
    DWORD   CRC
    DWORD   Memory
    WORD    Version  (0x0004)
    BYTE    Unknown  (0x00)
    BYTE    Unknown  (0x01)
    DWORD   Unknown  (always 1 for me, seen 0 as well)
    DWORD   Unknown  (always 0 for me, seen 1 and 2 as well)
    DWORD   Unknown  (0x00000000)
    DWORD   Unknown  (seen values between 15 and 32)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Hours per Day  (always 24 for me)
    BYTE    Unknown  (0x00)
    DWORD   Day of Year  (between 1 and 366, 1 for new cities)
    BYTE    Unknown  (0x00)
    DWORD   Week of Year  (between 1 and 53, 1 for new cities)
    BYTE    Unknown  (0x00)
    DWORD   Month of Year  (between 1 and 12, 0 for new cities)
    BYTE    Unknown  (0x00)
    DWORD   Year  (starts at 2000, 0 for new cities)
    BYTE    Unknown  (0x00)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Unknown  (0x00000000)
    BYTE    Unknown  (0x00)
    DWORD   Julian Date  (starts at 0x00256858)
