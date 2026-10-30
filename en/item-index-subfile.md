---
title: "Item Index Subfile"
description: ""
published: true
date: '2019-08-10T02:40:14Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T02:40:14Z'
---

This page pertains to the format of the **Item Index Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) *098F964D*. It can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. This particular subfile was decoded by .

## Structure

    DWORD   Subfile Size in bytes
    DWORD   CRC
    DWORD   Memory address
    WORD    Major Version  (0x0001)
    FLOAT32 City Width in metres  (1024, 2048 or 4096)
    FLOAT32 City Depth in metres  (1024, 2048 or 4096)
    DWORD   City Width in tracts  (16, 32 or 64)
    DWORD   City Depth in tracts  (16, 32 or 64)
    DWORD   City Width in tiles  (64, 128 or 256)
    DWORD   City Depth in tiles  (64, 128 or 256)
    DWORD   Count of Cell Columns  (always 192)
       DWORD    Count of Cell Rows  (always 192)
          DWORD Count of Cell Items  (number of records, each with two DWORDS)
             DWORD  Link: Memory Address
             DWORD  Link: Subfile Type ID

A city is laid out as a grid, 192x192 cells, regardless of its size. This index lists all items (buildings, props, effects, flora, etc.) that appear in each such cell. If an item spans several cells, it is listed in all those cells.

An empty city has all these records filled with a "Count of Cell Items" = 0. The total size of such a file thus becomes 148,266 bytes.
