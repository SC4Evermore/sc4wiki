---
title: "Pipe Occupant Subfile"
description: ""
published: false
date: '2021-07-06T19:33:21Z'
tags: []
editor: markdown
dateCreated: '2021-07-06T17:12:28Z'
---

This page pertains to the format of the **Pipe Occupant Subfile** within the [Savegame](/savegame) files. This file has [Type ID](/type-id) **0x49c05b9f** and was decoded by . The file contains information on how to render the underground pipes view.

## Structure

The structure of a record is very similar to the structure of the [Network Subfile 2](/network-subfiles#network-subfile-2-ca16374f).

    DWORD   Size
    DWORD   CRC
    DWORD   Memory address
    WORD    Major version
    WORD    Minor version
    BYTE    Zot byte
    BYTE    Unknown
    DWORD   Unknown
    BYTE    Apperance byte (always 0x05)
    DWORD   Unknown (always 0xc772bf98)
    BYTE    Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD    X Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    WORD    Z Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    DWORD   Count of Properties  (I've only seen 0x00000000)
        SGPROP  SaveGame Properties, repeated Count times
    DWORD   Group ID  (always 0x00000000)
    DWORD   Type ID  (always 0x00000000)
    DWORD   Instance ID  (always 0x00000000)
    BYTE    Unknown (always 0x05)

    # Next follow 9 floats, they represent a 2D transformation matrix, probably 
    # for the texture (though no texture is drawn for pipe occupants). Most of the 
    # time this is the identity matrix.
    9 x FLOAT

    FLOAT32 Center X coordinate
    FLOAT32 Center Y coordinate
    FLOAT32 Center Z coordinate

        # Next follows 4 times a data structure that contains information for
        # drawing a texture.
        3 x FLOAT32  (x, y, z) coordinates of the vertex
        2 x FLOAT32  (u, v) coordinates for texture mapping
        4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).

    DWORD   Id of pipe model to show. Seen several values (0x00004b00: straight 
            piece, 0x00020700: + piece, ...)
    5xBYTE  Unknown
    BYTE    Orientation
    3xBYTE  Unknown
    BYTE    Network Type (0x04)
    BYTE    Connection west  (0x02 for straight, 0x01 or 0x03 for diagonal)
    BYTE    Connection north (0x02 for straight, 0x01 or 0x03 for diagonal)
    BYTE    Connection east  (0x02 for straight, 0x01 or 0x03 for diagonal)
    BYTE    Connection south (0x02 for straight, 0x01 or 0x03 for diagonal)
    4xBYTE  Unknown
    FLOAT32 Xmin
    FLOAT32 Xmax
    FLOAT32 Ymin
    FLOAT32 Ymax
    FLOAT32 Zmin
    FLOAT32 Zmax
    3xBYTE  Unknown
    BYTE    Unknown (mostly 0x10, seen 0x12, 0x13, 0x14, 0x15) for diagonal tiles as well.
    4xDWORD Unknown
    DWORD   Unknown  (Always 50)
    DWORD   Unknown  (0x00000000)
    WORD    Unknown  (0x0000)
    FLOAT32 Unknown  (Normally 1)
    DWORD   Number of vertical side textures to draw (see below)

    # Below follow 5 arrays defining the sides of the hole. If an array is empty, 
    # there is no texture to be rendered at that side (typically for straight 
    # sections). Order is west, north, east, south, bottom.
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).

    DWORD   Unknown  (Always 0x00000000)

    # Next follow 16 floats, representing the values of the transformation matrix for the model
    #  | a b c d |
    #  | d e f g |
    #  | h i j k |
    #  | l m n o |
    # d, g and k are the translation components and are set to the position *in the city*.
    16 x FLOAT32

    DWORD    X Tile
    DWORD    Z Tile
    BOOLEAN  False if diagonal from NW to SE, true if diagonal from SW to NE
    BOOLEAN  False if this side is "off" for diagonal network
    BOOLEAN  False if this side is "off" for diagonal network (both true for straight and parallel diagonal network).
    FLOAT32  Y terrain coordinate of NW corner
    FLOAT32  Y terrain coordinate of SW corner
    FLOAT32  Y terrain coordinate of SE corner
    FLOAT32  Y terrain coordinate of SW corner
    FLOAT32  Y coordinate of the pipe model
    DWORD    Subfile ID (0x49c05b9f)
    DWORD    Unknown
    DWORD    Unknown
