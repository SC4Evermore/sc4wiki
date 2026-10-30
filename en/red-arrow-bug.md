---
title: "Red Arrow Bug"
description: ""
published: false
date: '2019-08-09T09:43:27Z'
tags: ["Bugs"]
editor: markdown
dateCreated: '2008-07-28T07:31:31Z'
---

This bug happens when the [NAM](/nam) isn't installed properly. It makes all or some of the [puzzle pieces](/puzzle-piece) become "non-ploppable"

This bug can also be caused if a certain plugin file is outdated and/or conflicting with the NAM. Reading the file's readme or running the [BSC Cleanitol](/bsc-cleanitol) program is often the best way to fix this problem.

## Information

The only thing which can cause the red arrow bug is the presence of obsolete and outdated "high-level" ([RUL](/rul-file)-based) transit mods in your Plugins folder, which are conflicting with the current [NAM](/nam).

**What can cause Red Arrow Bug:**

- Past versions of the NAM
- [DatPacked](/datpacker) NAM files
- Versions of the RHW released prior to June 1, 2007 (v13a and earlier)
- NAM_Override_FencedGLR.dat (included with [cogeo](/people/cogeo)'s [Fenced GLR Puzzle Pieces](/plugin/fenced-glr-puzzle-pieces)--which are otherwise compatible with the current NAM without this file
- Old [GLR](/glr) Neighbour Connection fixes (Z_Connector.dat and Z_Connector_Jan 07.dat)
- Transit SuperMod by [DarkMatter](/people/darkmatter) (pre-NAM)
- Transit BugFix by [the7trumpets](/people/the7trumpets) (pre-NAM)
- Transit BugFix Supplement by [redlotus](/people/redlotus) (pre-NAM)

To solve this issue, remove these files from your Plugins. You can use the [BSC Cleanitol](/bsc-nhp-cleanitol) program, with the included NAM Cleanitol List (included with the NAM Download), which will remove all these outdated files automatically. Please also note that the list above is potentially incomplete.

**What cannot cause Red Arrow Bug**

- Stations
- Texture Mods (i.e. [SFBT](/sfbt) [Euro Road Textures Mod](/plugin/sbft-euro-road-textures-mod), [Shadow Assassin's](/people/shadow-assassin) [RHW replacement textures](/plugin/sa-rhw-texture-replacement), etc.)
- Transit Switch/Underpass Lots (i.e. [blahdy's](/people/blahdy) [Big Dig](/plugin/big-dig-project), [buddybuds's](/people/buddybud) [Underpasses](/plugin/buddybud-underpass), [Marrast's](/people/marrast) [MTEL](/plugin/mtel), etc.)

## Technical Info

RUL Files are SC4 files which control the placement of transit networks in-game, including both draggabble networks and puzzle pieces. Some bridges are also RUL-controlled. Each one has a specific function, and the game can only read one copy of each of these RUL files. When you are getting the red arrow bug, it means that the game is loading a RUL file which does not reference the puzzle piece you are trying to place in game.

> **Note:** This article needs expanding.
