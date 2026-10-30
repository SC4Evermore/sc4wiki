---
title: "INI"
description: ""
published: false
date: '2019-08-09T02:55:09Z'
tags: ["File Formats/COMM", "Modding", "MTS2"]
editor: markdown
dateCreated: '2009-01-06T16:50:38Z'
---

**INI** files are initialization files, which generally refer to any INI script used in [SimCity 4](/simcity-4). They often occur within [DBPF](/dbpf) files, however, as a common file type, there are also some that are loose files associated with the game. Some of the INI files used by the game are rather complex, and have been given their own article, others are described below.

## INIs Within DBPFs

As mentioned above, INI files are often located within DBPF files, and control a wide variety of game properties. They are listed below.

| Type ID | Group ID | Instance ID | Name | Description |
|----|----|----|----|----|
| 0x00000000 | 0x4a87bfe8 | 0x2a87bffc | [Font Table](/font-table) | Defines font properties for use in-game. |
| 0x00000000 | 0x8a5971c5 | 0x2b563701 | Expansion Pack INI | Enables and disables expansion pack features. |
| 0x00000000 | 0x8a5971c5 | 0x8a5993b9 | [Network INI](/network-ini) (aka Remapping) | Contains parameters related to networks. |
| 0x00000000 | 0x8a5971c5 | 0xaa597172 | [Terrain Texture File](/terrain-texture-file) | Contains tunable parameters related to terrain. |
| 0x00000000 | 0x8a5971c5 | 0xea8a1115 | Sound Config | Contains properties related to in-game sounds. |

It should also be noted that [RUL](/rul) files often bear a close resemblance to INI files, but are covered elsewhere.

## Loose INIs

Both SimCity 4 itself, and the Maxis created add-on programs, contain a variety of loose INI files. They are listed below.

- *SimCity 4.ini* - Defines locations of files for the game.
- *region.ini* - Included with every region, it contains basic information, such as the Region name.
- *Ingred.ini* - Contains a lot of information for deciphering other files.
- *LotEditor.ini* - Defines locations of files for [Lot Editor](/lot-editor) as well as Occupant Groups.

### region.ini

Region.ini files all have the same format, with the following four fields.

    [Regional Settings]
    Name = #0x4ab6d262   (Can be name in plain text, or an LTEXT reference as seen here)
    Terrain type = 0     (Toggles water or land for a new region)
    Water Min = 60       (Sets the lower value for Moisture content when rendering a map from grayscale)
    Water Max = 100      (Sets the upper vlaue for Moisture content when rendering a map from grayscale)

Note: *The Water Min and Water Max are only implemented when rendering a map from a grayscale image using Shift-Ctrl-Alt-R in region view.*

Sample Pics:

July 11 Moisture, Water Min = **60**, Water Max = **100** :

<http://i128.photobucket.com/albums/p184/CorinaPics/01%2060-100%2007-11_zpstiwwfbdq.jpg>

July 11 Moisture, Water Min = **60**, Water Max = **200** :

<http://i128.photobucket.com/albums/p184/CorinaPics/03%2060-200%2007-11_zpsgghmf28h.jpg>

July 11 Moisture, Water Min = **30**, Water Max = **150** :

<http://i128.photobucket.com/albums/p184/CorinaPics/02%2030-150%2007-11_zpscxibltci.jpg>

Above images created using: <http://community.simtropolis.com/files/file/31154-coris-dataview-moisture/>
