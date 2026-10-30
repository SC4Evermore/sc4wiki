---
title: "FSH"
description: ""
published: true
date: '2019-08-09T02:54:55Z'
tags: ["File Formats/SC4"]
editor: markdown
dateCreated: '2008-10-01T20:10:50Z'
---

**FSH** files are texture files. The FSH abbreviation comes from Franks SHape files. They represent most of the textures used in [SimCity 4](/simcity-4), including network textures. An explanation of their format can be found at [FSH Format](/fsh-format). See [Tutorial:Creating Textures](/tutorial/creating-textures) for information about creating textures, focused on transit textures.

## Group IDs of FSH Files

FSH files are collected into the following [Group IDs](/group-id) based on their use.

`0x0986135E - Base and Overlay Lot Textures`  
`0x1ABE787D - Transit Textures/Buildings/Bridges/Misc`  
`0x2A2458F9 - Animation Sprites (Props)`  
`0x2BC2759A - Transit Network Shadows (Masks)`  
`0x49A593E7 - Animation Sprites (Non Props)`  
`0x891B0E1A - Terrain And Foundations`  
`0xCB6B7BD9 - LE Arrow Images`  
`0x46A006B0 - User Interface Images`

FSH files may also have unique groups for user created custom content textures.

## Parents

FSH files can be called by several file types, see [Relations](/relations) for more information. Possible parents include:

- S3D Files
- RUL Files
- Animation (ATC/AVP?)
