---
title: "BMP"
description: ""
published: false
date: '2019-08-09T02:55:09Z'
tags: ["File Formats/COMM", "MTS2"]
editor: markdown
dateCreated: '2009-01-06T16:44:12Z'
---

**BMP** is the file extension for bitmap files, or raw image data. More information about their technical specifications in general usage can be found at [Wikipedia's article on Bitmaps](/wikipedia-bitmap).

Within [SimCity 4](/simcity-4) itself, they are rarely used. Some of the ways the game uses them include: intro slides and the config.bmp file. Simcity_1.dat contains several files that are initially listed as being BMP files when the file is opened in iLive's [Reader](/reader), but after being selected show as being either [PNG](/png) or [JFIF](/jfif) files.

## config.bmp

**config.bmp** is one of the two critical files for any region (the other being region.ini), and it carries information about city tile size and location within the region. config.bmp is a 24-bit (or less) bitmap, where each pixel corresponds to a small city tile in the game. The color assigned to any pixel determines whether that location in the region belongs to a small, medium, or large city tile.

Blue pixels denote large city tiles, and must be in groups of 16 square pixels (4 px X 4px square). The color can be any shade of blue so long as the color has an RGB format of xxx,xxx,255 (xxxxFF in hex) - where xxx can be any number except 255.

Green pixels denote medium city tiles, and must be in groups of 4 square pixels (2px X 2px square). The color can be any shade of green so long as the color has an RGB format of xxx,255,xxx (xxFFxx in hex) - where xxx can be any number except 255.

Red pixels denote small city tiles, and are always in single pixel groups. The color can be any shade of red so long as the color has an RGB format of 255,xxx,xxx (FFxxxx in hex) - where xxx can be any number except 255.

Generally, using the RGB format above, xxx = 000, so that the three colors used are true red, green, and blue - however for larger config.bmp files it can be helpful to tile the colors within the acceptable range of colors for a particular city size. The *Protect City* screen that loads after selecting a region in [SC4Terraformer](/sc4terraformer) shows an example of color tiling.

Additionally, the location of city tiles (as represented by colored squares) within the config.bmp file must be such that every pixel has an acceptable color assigned to it, so that the game can create the corresponding city size. For example, a blue square that was 3 pixels on each side would not be recognized by the game. Likewise, green and blue squares that are any shape other than square will not be recognized by the game.

There is no limit on the dimensions of a config.bmp file, other than that it must be either a rectangle or square. However, as one pixel corresponds to a small sized city tile, these files tend to be relatively small, even for large regions.
