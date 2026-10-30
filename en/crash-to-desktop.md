---
title: "Crash To Desktop"
description: ""
published: true
date: '2019-08-09T09:43:26Z'
tags: ["Bugs"]
editor: markdown
dateCreated: '2008-06-29T12:06:39Z'
---

> **Note:** This article needs expanding.

A **Crash to Desktop**, abbreviated as **CTD**, is the name for when the game unexpectedly closes and returns you to the desktop.

## Commonly Known Causes of CTD's

- Zooming in or out rapidly. Zooming requires the game to regenerate the graphics at a new zoom, which can overwhelm the program.
- Making contact between [Puzzle Pieces](/puzzle-piece) and [Transit Enabled](/transit-enabled) (TE) lots.
- Functional Landmarks Mod, while you still have normal, non-functional Landmarks in your city.
- There may be others not listed here.

### Puzzle Piece & Transit Enabled Lot Conflict

\[<http://sc4devotion.com/forums/index.php?topic=5094.0>\| NAM FAQ\] This issue occurs only when a [Puzzle Piece](/puzzle-piece) of a certain network is hovered over a [Transit Enabled](/transit-enabled) lot that is transit enabled with the same network. For example, Elevated Heavy Rail Viaducts over a Transit-Enabled Rail Station.

The issue is the result of hardcoded material in the main .exe file; the SimCity 4.exe file, for some reason or another, tends to get stuck in an "infinite loop" when puzzle pieces are hovered over [TE Lots](/te-lot). The infinite loop causes an exception and the game closes itself automatically due to this.

It was previously thought to be unfixable due to it's hardcoded nature, until [Simmaster07](/people/simmaster07) discovered a solution via DLL modding. The DLL SC4 Fix completely removes the crashing due the TE Lot/Puzzle Piece hovering, and also stabilizes other aspects of the game, making CTDs generally less likely, though still possible (e.g. zooming in/out too fast). You can download it from the STEX \[<http://community.simtropolis.com/files/file/30883-sc4fix-third-party-patches-for-sc4/>\| here\], though please note that, as of May 2016, the NAM RHW Disconnector tool still caused CTDs with *all* TE Lots, regardless of network type.

For more info on TE Lots, see [mott](/people/mott)'s discussion on the topic [1](http://sc4devotion.com/forums/index.php?topic=2763.0). Thanks to [Chrisim](/people/chrisim) for providing some additional information on this issue!

> **Note:** This article needs expanding.
