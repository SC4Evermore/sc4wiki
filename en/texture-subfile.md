---
title: "Texture Subfile"
description: ""
published: false
date: '2024-03-03T14:24:43Z'
tags: []
editor: markdown
dateCreated: '2020-03-14T12:47:16Z'
---

This page pertains to the format of the **Texture** Subfile within the Savegame files. This file has Type ID **c97f987c**. This particular subfile was decoded by .

## Description

This subfile contains data about the textures in the city. For every lot in the city 1 texture record exists. Within every texture record is a list of all textures used on the lot, both base and overlay textures.

## Structure

The Texture subfile has the following format:

    DWORD   Size    
    DWORD   CRC 
    DWORD   Memory  
    WORD    Major version (0x0002)  
    WORD    Minor version (0x0004)  
    BYTE    Unknown, only seen 0x00 
    BYTE    Unknown, only seen 0x00 
    BYTE    Unknown, only seen 0x00 
    BYTE    Unknown, mostly 0x05, probably an appearance flag. (A)
    DWORD   Unknown, always 0x497f6d9d
    BYTE    Min Tract X (normally between 0x40 and 0x7f)    
    BYTE    Min Tract Z (normally between 0x40 and 0x7f)    
    BYTE    Max Tract X (normally between 0x40 and 0x7f)    
    BYTE    Max Tract X (normally between 0x40 and 0x7f)    
    WORD    X Tract Size? (only seen 0x0002, probably indicating the size is 2²)    
    WORD    Z Tract Size? (only seen 0x0002, probably indicating the size is 2²)    
    DWORD   Unknown, only seen 0x00000000   
    DWORD   Unknown, only seen 0x00000000   
    DWORD   Unknown, only seen 0x00000000   
    DWORD   Unknown, only seen 0x00000000   
    FLOAT32 Min X Coordinate    
    FLOAT32 Min Y Coordinate    
    FLOAT32 Min Z Coordinate    
    FLOAT32 Max X Coordinate    
    FLOAT32 Max Y Coordinate    
    FLOAT32 Max Z Coordinate    
    BYTE    Unknown, seen 0x01 and 0x02 
    DWORD   Count of tiles with a texture   
        DWORD   Instance ID of the texture
        BYTE    X tile
        BYTE    Z tile
        BYTE    Orientation
        BYTE    Priority 0x00 for base texture, 0x01 for overlay texture (actually rather seems to indicate mirroring of the texture)
        4 BYTES RGBA, see below
        BYTE    Unknown, mostly 0xff but seen 0x03 and 0x01 as well
        BYTE    Texture variation, see below

### RGBA

The RGBA bytes can be used to change the color of the texture. They are mostly set to 0xff 0xff 0xff 0xff, but the game sets them to green values for residential zones, blue values for commercial zones etc.

### Texture variation

The texture variation byte indicates what texture variant of the texture family the game was using when it created the Savegame. Setting this value does not seem to have any influence as the game randomly picks a texture variant from the family when opening up a city, and even when saving a city.

## Remarks

Byte (A) is probably an appearance flag in the same way an appearance flag is used in the [Prop Subfile](/prop-subfile). It is mostly set to **0x05**, or **0b00000101**.
