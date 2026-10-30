---
title: "Network Subfiles"
description: ""
published: false
date: '2024-12-21T09:21:07Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2012-09-28T20:04:09Z'
---

This page pertains to the format of the **Network Subfiles** within the [Savegame](/savegame) files. These files have [Type IDs](/type-id) *6A0F82B2* (Network Index), *C9C05C6E* (Network Subfile 1) and *CA16374F* (Network Subfile 2). They can be viewed using the [SC4 Savegame Explorer](/sc4-savegame-explorer), but not edited. These subfiles were decoded by and completed by .

# Network Index Subfile (6A0F82B2)

## Description

This index file contains a list of all network tiles, with links to the two network files where the records can be found.

## Network Index Subfile Structure

### Network Index Subfile Body

    DWORD   Subfile Size in bytes
    DWORD   CRC
    DWORD   Memory address
    WORD    Major Version  (0x0007 for built cities, but 0x0003 for Maxis' own, unbuilt cities)
    DWORD   City Tile Count  (4096, 16384 or 65536 depending on city size)
    DWORD   Count of Network Tiles  (0 for a new city)
       DWORD    Tile Number  (See Appendix 1.1 for more information)
       DWORD    Link: Memory address
       DWORD    Link: Subfile Type ID
       DWORD    Count of blocks  (either 0 or 10)
          DWORD Block Number (first one is 0, last one is 9)
          DWORD Count  (anything between 0-16. Number of byte blocks)
             BYTE×8     Unknown block of bytes. Small numbers < 10
       DWORD        Count of pointers to follow
          DWORD     Memory address of automata
          DWORD     Type ID of automata. Seen 0x896e75af (cSC4Pedestrian), 0x4a416254 (cSC4TrainCard),
                    0x896e714a (cSC4Vehicle), 0xaa9f4a3d (cSC4Bus) and 0x4a5b69ed (cSC4TrailerVehicle).
                    Other automata might exist as well, refer to all Type ids in Savegames.
       BYTE Unknown  (always 0x00)
       DWORD    Unknown  (Seen 0 and 2)
       DWORD    Unknown  (Only seen 2)
       DWORD    Unknown  (Seen 0 and 4)
       FLOAT32  Unknown  (Small values, e.g. 0.0, 2.0, 5.0, 6.0, 8.0)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       FLOAT32  Unknown  (Small values, e.g. 0.0, 2.0, 5.0, 6.0, 8.0)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       FLOAT32  Unknown  (Small values, e.g. 0.0, 2.0, 5.0, 6.0, 8.0)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       FLOAT32  Unknown  (Small values, e.g. 0.0, 2.0, 5.0, 6.0, 8.0)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (0 or 1)
       WORD Unknown  (always 0)
       DWORD    Count of blocks to follow
           DWORD    Block number
           FLOAT32  Unknown
           WORD     Unknown (only seen 0x00)
    DWORD           Count of network intersections (such as + and T intersections) in city
       DWORD        Link: Memory address
       DWORD        Link: Subfile Type ID of a network subfile
       BYTE         Unknown  (only seen 0x00)
       DWORD        Count of blocks to follow  (only seen 0 or 1)
          DWORD     Memory address
          DWORD     Subfile Type ID (only seen 0x4c22ae53 Mass Transit Train)

       # The values below seem to indicate what directions are enabled on this
       # network. That's why they are repeated 4 times for west, north, east
       # and south.
          DWORD     Tentatively indicates how many of following floats are meaningful (0, 1, 2 or 3).
          BOOLEAN   Unknown (either 0 or 1)
          FLOAT32×3 Unknown (often small values such as 0.0, 1.2, 6.0, 8.0)

    DWORD   Count of transit-enabled lot tiles to follow
       WORD         Z tile
       WORD         X tile
       DWORD        Unknown (always 0x00000001)
       DWORD        Memory address of network tile
       DWORD        Type ID of network (0xc9c05c6e)
    DWORD   Unknown  (only seen 0x00000000)
    DWORD   Unknown  (only seen 0x00000000)
    DWORD   Tile X  (63, 127 or 255 for a new city, smaller for built up cities, probably max coordinate that ever has had a network)
    DWORD   Tile Z  (63, 127 or 255 for a new city, smaller for built up cities, probably max coordinate that ever has had a network)
    FLOAT32 Unknown  (Small value. 0.00 for a new city)
    BOOLEAN Unknown  (always 1, true)
    FLOAT32 Unknown  (Small value. 0.00 for a new city)
    BOOLEAN Unknown  (always 1, true)
    DWORD   Count of blocks to follow  (Does not appear if version = 0x0003)
       DWORD         Memory address
       DWORD         Type ID of network (seen 0xc9c05c6e and 0x49c1a034).
       DWORD         Count of DWORDs to follow (only seen 0x00000000 though)
           DWORD     Unknown (never seen, but assumed, see below)
       WORD          Unknown (all kinds of values, change when saving without doing anything)
       DWORD         Count of DWORDs to follow
           DWORD     Unknown, might as well be 4 bytes
       WORD          Unknown (all kinds of values, change when saving without doing anything)
       DWORD         Count of DWORDs to follow
           DWORD     Unknown, might as well be 4 bytes
       WORD          Unknown (all kinds of values, change when saving without doing anything)
       DWORD         Count of DWORDs to follow
           DWORD     Unknown, might as well be 4 bytes
       WORD          Unknown (all kinds of values, change when saving without doing anything)

### Appendix 1.1

Tile numbering starts in the NW corner, which is tile number *0x00000000*.

- Tile number *0x00000001* is to the east of that tile.
- In a small city, the first tile in the second row is *0x00000040*.
- In a medium city, the first tile in the second row is *0x00000080*.
- In a large city, the first tile in the second row is *0x00000100*.
- In a small city, the last tile in the last row is *0x00000FFF*.
- In a medium city, the last tile in the last row is *0x00003FFF*.
- In a large city, the last tile in the last row is *0x0000FFFF*.

# Network Subfile 1 (C9C05C6E)

## Structure

### Network Subfile 1 Body

List of texture-based network tiles consisting of records of the form:

    DWORD   Record Size
    DWORD   CRC
    DWORD   Memory
    WORD×2  Version (always 8, 4)
    DWORD   Appearance Flags  (Always 0x05000000)  (See Appendix 2.2 for more information)
    DWORD   0xC772BF98  (always the same)
    BYTE    Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD    X Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    WORD    Z Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    DWORD   Count of Properties
        SGPROP      SaveGame Properties, repeated Count times  (See Appendix 2.1 for more information)
    DWORD   Group ID  (always 0x00000000)
    DWORD   Type ID  (always 0x00000000)
    DWORD   Instance ID  (always 0x00000000)
    BYTE    Unknown Flag (0 or 1)
    FLOAT32 X Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Z Coordinate

        # Next follows 4 times a data structure that contains information for
        # drawing a texture.
        3 x FLOAT32  (x, y, z) coordinates of the vertex
        2 x FLOAT32  (u, v) coordinates for texture mapping
        4 x BYTE     (r, g, b, a) values indicating a color (always #dedbddff).

    DWORD   TextureID / PathID
    BYTE    Wealth texture  (See Appendix 2.6)
    DWORD   Base texture  (See Appendix 2.7)
    BYTE    Orientation  (See Appendix 2.3 for more information)
    BYTES×2 Unknown  (Small values)
    Byte    Flag for crossings (1 = crossings of two networks, 0 = single network)
        BYTE    Network Type  (See Appendix 2.4 for more information)
        BYTE    Connection, West  (See Appendix 2.5 for more information)
        BYTE    Connection, North  (See Appendix 2.5 for more information)
        BYTE    Connection, East  (See Appendix 2.5 for more information)
        BYTE    Connection, South  (See Appendix 2.5 for more information)
    DWORD   Number of blocks for retaining walls
        DWORD   Retaining wall texture IID (See Appendix 2.9)
        # Followed by three vertex blocks of the form:
            Float32×5    (x, y, z, u, v) coordinates
            BYTE×4       (r, g, b, a) color
    FLOAT32 Xmin
    FLOAT32 Xmax
    FLOAT32 Ymin
    FLOAT32 Ymax
    FLOAT32 Zmin
    FLOAT32 Zmax
    DWORD   Construction states (See Appendix 2.8)
    DWORD   Alternate path ID (derived from AutoPathBase or TE-Lot), otherwise 0
    DWORD×3 Unknown  (All 0)
    INT64   Demolishing costs (See Appendix 2.10)

### Appendix 2.1 - Structure of SGPROP (SaveGame Properties)

    DWORD   Property Name Value
    DWORD   Property Name Value  (doubled for some unknown reason)
    DWORD   0x00000000
    BYTE    Data Type, 01=UInt8, 02=UInt16, 03=UInt32, 07=SInt32, 08=SInt64, 09=Float32, 0B=Boolean
    BYTE    KeyType, 0x00 = 0 reps, 0x80 = more than 0 reps
    WORD    0x0000
    DWORD   Rep Count  (this one appears only if KeyType = 0x80)
        DATA    Property Value (repeated Rep Count times, type according to Data Type)

#### SaveGame Properties

Properties known to appear on network tiles are listed below (See also the [Prop Subfile](/prop-subfile#savegame-properties-28sgprops-29)).

    0x4835C6A6 (Boolean) = Unknown (1?)
    0x4835C6A7 (UInt32×2) = TE-Lot network flags:
        DWORD - Unknown (0?)
        DWORD - Flags (0xSSEENNWW) (0x00000000 if custom path is used)
    0x4835C6A9 (UInt32) = TE-Lot custom path IID
    0x4835C6AA (Byte) = Bitmask for Onewayroad directions:
        0b00000001 - Edge West: direction West to East
        0b00000010 - Edge West: direction East to West
        0b00000100 - Edge North: direction North to South
        0b00001000 - Edge North: direction South to North
        0b00010000 - Edge East: direction West to East
        0b00100000 - Edge East: direction East to West
        0b01000000 - Edge South: direction North to South
        0b10000000 - Edge South: direction South to North
    0x4835C6AB (UInt32) = Unknown (some flags related to puzzle pieces?)
    0xAA24AE57 (UInt32) = Unknown (0?)

### Appendix 2.2 - Appearance Flags

        0x01000000 - Render the network shadow
        0x04000000 - Render the network

### Appendix 2.3 - Orientation

        0x00 = North
        0x01 = East
        0x02 = South
        0x03 = West
        0x80 = North, mirrored
        0x81 = East, mirrored
        0x82 = South, mirrored
        0x83 = West, mirrored

### Appendix 2.4 - Network Type

        0x00 = Road
        0x01 = Rail
        0x02 = Elevated Highway
        0x03 = Street
        0x04 = Pipe
        0x05 = Powerline
        0x06 = Avenue
        0x07 = Subway
        0x08 = Lightrail
        0x09 = Monorail
        0x0a = Onewayroad
        0x0b = Dirtroad
        0x0c = Ground Highway

### Appendix 2.5 - Connections

The [Network Flags](/network-flags) are denoted in octal representation in RUL files:

    0x00 = 0o00 (no connection)
    0x01 = 0o01 (diagonal left)
    0x02 = 0o02 (orthogonal)
    0x03 = 0o03 (diagonal right)
    0x04 = 0o04 (median)
    0x09 = 0o11 (blend left)
    0x0b = 0o13 (blend right)
    0x11 = 0o21 (diagonal switch left)
    0x13 = 0o23 (diagonal switch right)
    ...
    0x32 = 0o62 (wye)
    ...

### Appendix 2.6 - Wealth Textures

    0 = default texture
    1 = grass/low density $
    2 = grass/low density $$
    3 = grass/low density $$$
    4 = medium/high density $
    5 = medium/high density $$
    6 = medium/high density $$$
    7 = I-ag/landfill

### Appendix 2.7 - Base textures

    0x00000000 = None
    0x08100000 = Pavement $
    0x08200000 = Pavement $$
    0x08300000 = Pavement $$$
    0x08400000 = Dirt

### Appendix 2.8 - Construction states

This bitset encodes which networks are present on the tile, whether the tile has been fully constructed, as well as several other flags. Some dual-networks like HRW built by the over-click method can only be seen here.

    0x00000001 = Road (bit 0)
    0x00000002 = Rail (bit 1)
    0x00000004 = Highway (bit 2)
    ...  (see Appendix 2.4)
    0x00000800 = Dirtroad (bit 11)
    0x00001000 = Ground Highway (bit 12)
    ---
    0x00002000 = matching path file exists (for TE tiles: set if fully connected to network)
    0x00004000 = network not fully constructed yet (always set for TE tiles?)
    0x00008000 = rendering state (set if tile has been displayed since last rotation of the map)
    ---
    0x00040000 = bridge (...tentatively)
    0x00080000 = alpha off (for tunnel portal)
    0x00100000 = blue auto-place preview effect (set for all static puzzle pieces)
    0x00200000 = TE tile
    0x00400000 = anchored tile (static puzzle piece/tunnel portal)
    0x00800000 = tunnel portal
    0x01000000 = terrain triangles transposed
    0x02000000 = render western triangle of base and overlay, hole if 0
                 (set for texure-based tiles and for model-based tiles with wealth textures, not set for TE tiles)
    0x04000000 = render eastern triangle of base and overlay, hole if 0
                 (set for texure-based tiles and for model-based tiles with wealth textures, not set for TE tiles)
    0x08000000 = render terrain
                 (set for model-based network tiles and TE tiles, not set for purely texture-based tiles)
    0x10000000 = network fully constructed (for TE tiles: set if fully connected to network)
    0x20000000 = is lit
    0x40000000 = alpha off (for retaining wall/pillar)

### Appendix 2.9 - Retaining wall textures

    0x00BB0000 - retaining wall
    0x00BB0200 - railing
    0x08080000 - pillar
    0x0912220E - concrete

### Appendix 2.10 - Demolishing costs

The game has a strange quirk in the sense that it stores the demolishing costs as a \*signed\* 64 bit LE integer, but it shows it as an \*unsigned\* 32 bit LE integer when hovering with the bulldoze tool. This means that it supports a demolishing cost of e.g. -1, which will actually increase your city budget, but it will show §4,294,967,295 as demolishing cost. Perhaps that the people responsible for the gui thought it was a uint32, while it was actually meant as an sint64 by the programmers of the data structures?

# Network Subfile 2 (CA16374F)

This subfile contains network tiles related to the subway network and is similar to the [Pipe Occupant Subfile](/pipe-occupant-subfile).

## Network Subfile 2 Structure

List of records of the form:

### Network Subfile 2 Body

    DWORD   Record Size
    DWORD   CRC
    DWORD   Memory
    WORD×4  Version (always 2, 3, 8, 4)
    DWORD   Appearance Flags  (Always 0x05000000)  (See Appendix 2.2 for more information)
    DWORD   0xC772BF98  (always the same)
    BYTE    Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE    Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD    X Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    WORD    Z Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    DWORD   Count of Properties  (I've only seen 0x00000000)
        SGPROP      SaveGame Properties, repeated Count times  (See Appendix 2.1 for more information)
    DWORD   Group ID  (always 0x00000000)
    DWORD   Type ID  (always 0x00000000)
    DWORD   Instance ID  (always 0x00000000)
    BYTE    Unknown  (Always 0x05)
    FLOAT32 Unknown  (Normally 0, -1 or 1)
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 0, -1 or 1)
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 1)
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 0, -1 or 1)
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 0, -1 or 1)
    FLOAT32 Xmax
    FLOAT32 Ymax
    FLOAT32 Zmax
    FLOAT32 Xmin
    FLOAT32 Ymin
    FLOAT32 Zmin
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 0)
    DWORD   Unknown  (Always 0xFF000000)
    FLOAT32 X Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Z Coordinate
    FLOAT32 Unknown  (Normally 0)
    FLOAT32 Unknown  (Normally 1)
    DWORD   Unknown  (Always 0xFF000000)
    FLOAT32 X Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Z Coordinate
    FLOAT32 Unknown  (Normally 1)
    FLOAT32 Unknown  (Normally 1)
    DWORD   Unknown  (Always 0xFF000000)
    FLOAT32 X Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Z Coordinate
    FLOAT32 Unknown  (Normally 1)
    FLOAT32 Unknown  (Normally 0)
    DWORD   Unknown  (Always 0xFF000000)
    DWORD   TextureID / PathID
    BYTES×5 Unknown  (Small values)
    BYTE    Orientation  (See Appendix 2.3 for more information)
    BYTES×3 Unknown  (Small values)
    BYTE    Network Type  (See Appendix 2.4 for more information)
    BYTE    Connection, West  (See Appendix 2.5 for more information)
    BYTE    Connection, North  (See Appendix 2.5 for more information)
    BYTE    Connection, East  (See Appendix 2.5 for more information)
    BYTE    Connection, South  (See Appendix 2.5 for more information)
    BYTES×4 Unknown  (Small values)
    FLOAT32 Xmin
    FLOAT32 Xmax
    FLOAT32 Ymin
    FLOAT32 Ymax
    FLOAT32 Zmin
    FLOAT32 Zmax
    BYTE    Unknown  (Always 128)
    BYTE    Unknown  (Always 32)
    BYTE    Unknown  (Always 0)
    BYTE    Unknown  (Seen 16-21)
    DWORD×4 Unknown  (All 0)
    DWORD   Demolishing costs
    DWORD   Unknown  (0x00000000)
    WORD    Unknown  (0x0000)
    FLOAT32 Unknown  (Normally 1)
    DWORD   Number of extra blocks  (0, 1, 2 or 3)

    # Below follow 5 arrays defining the sides of the hole. If an array is empty, there is
    # no texture to be rendered at that side (typically for straight sections). Order is
    # west, north, east, south, bottom.
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping (normally 0, 0.75 or 1)
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping (normally 0, 0.75 or 1)
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping (normally 0, 0.75 or 1)
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping (normally 0, 0.75 or 1)
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).
    DWORD   Count  (Either 0 or 4)
       3 x FLOAT32  (x, y, z) coordinates of the vertex
       2 x FLOAT32  (u, v) coordinates for texture mapping (normally 0, 0.75 or 1)
       4 x BYTE     (r, g, b, a) values indicating a color (either #ffffffff or #ffffff80).

    DWORD   Unknown  (Always 0x00000000)

    # Next follow 16 floats, representing the values of the transformation matrix for the model
    #  | a b c d |
    #  | d e f g |
    #  | h i j k |
    #  | l m n o |
    # d, g and k are the translation components and are set to the position *in the city*.
    16 x FLOAT32

    DWORD   X Tile
    DWORD   Z Tile
    BOOLEAN Unknown  (Always 0)
    BOOLEAN Unknown  (Either 0 or 1, false or true)
    BOOLEAN Unknown  (Either 0 or 1, false or true)
    FLOAT32 Y Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Y Coordinate
    FLOAT32 Y Coordinate
    DWORD   0xCA16374F  (Subfile ID)
    DWORD   0x00000000  (always the same)

# Prebuilt Network Subfile (0x49c1a034)

The prebuilt network subfile contains all model-based network tiles with a prefabricated model, such as elevated highways and monorail.

## Structure

List of records of the form:

    DWORD    Size
    DWORD    CRC
    DWORD    Memory
    WORD×3   Version (always 4, 8, 4)
    DWORD    Appearance flags (0x05000000)  (See Appendix 2.2 for more information)
    DWORD    Unknown (always 0xc772bf98)
    BYTE     Min Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE     Min Tract Z Coordinate  (normally between 0x40 and 0x7F)
    BYTE     Max Tract X Coordinate  (normally between 0x40 and 0x7F)
    BYTE     Max Tract Z Coordinate  (normally between 0x40 and 0x7F)
    WORD     X Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    WORD     Z Tract Size (power of 2)  (only seen 0x0002 ... 2² = 4 tiles)
    DWORD    Count of Properties
        SGPROP      SaveGame Properties, repeated Count times
    DWORD    Group ID of Network Model Exemplar (see Appendix 4.1)
    DWORD    Type ID of Network Model Exemplar (0x6534284a)
    DWORD    Instance ID of Network Model Exemplar
    BYTE     Matrix flag (1 = no matrix, 5 = matrix is present)
        FLOAT32×9   Transformation matrix
    FLOAT32  X Coordinate
    FLOAT32  Y Coordinate
    FLOAT32  Z Coordinate

        # Next follows 4 times a data structure that contains information for
        # drawing a texture.
        3 x FLOAT32  (x, y, z) coordinates of the vertex
        2 x FLOAT32  (u, v) coordinates for texture mapping
        4 x BYTE     (r, g, b, a) values indicating a color (always #dedbddff).

    DWORD   TextureID / PathID
    BYTE    Wealth texture  (See Appendix 2.6)
    DWORD   Base texture  (See Appendix 2.7)
    BYTE    Orientation
    BYTES×2 Unknown  (Small values)
    Byte    Flag for crossings (1 for crossings of two networks, 0 for single network)
        BYTE    Network Type  (See Appendix 2.4 for more information)
        BYTE    Connection, West  (See Appendix 2.5 for more information)
        BYTE    Connection, North  (See Appendix 2.5 for more information)
        BYTE    Connection, East  (See Appendix 2.5 for more information)
        BYTE    Connection, South  (See Appendix 2.5 for more information)
    DWORD   Number of blocks for retaining walls (always 0 for model-based network tiles)
        DWORD   Retaining wall texture IID (See Appendix 2.9)
        # Followed by three vertex blocks of the form:
            Float32×5    (x, y, z, u, v) coordinates
            BYTE×4       (r, g, b, a) color
    FLOAT32 Xmin
    FLOAT32 Xmax
    FLOAT32 Ymin
    FLOAT32 Ymax
    FLOAT32 Zmin
    FLOAT32 Zmax
    DWORD   Construction states (See Appendix 2.8)
    DWORD   Path ID derived from AutoPathBase, otherwise 0
    DWORD×3 Unknown (apparently always 0x00000000)
    INT64   Demolishing costs (see Appendix 2.10)
    FLOAT32×3  Unknown (usually 0 or very small -- seem to be related to matrix)
    BYTE×5  Unknown (apparently always 0x00)
    DWORD   pillar ID (if non-zero, it is followed by a block):
        FLOAT32 pillar rotation
        FLOAT32 pillar offset X
        FLOAT32 pillar offset Y
        FLOAT32 pillar offset Z

## Appendix 4.1 - Network Model Exemplars

For a list of Group IDs, see [Model Exemplar](/model-exemplar).

# Network Bridge Subfile (0x49cc1bcd)

Apparently exactly the same structure as the [prebuilt network subfile](/network-subfiles#prebuilt-network-subfile-0x49c1a034).

# Network Tunnel Subfile (0x8a4bd52b)

## Structure

List of records of the form:

    DWORD    Size
    DWORD    CRC
    DWORD    Memory
    WORD×4   Version (always 2, 4, 8, 4)
    DWORD    Appearance flags (0x05000000)  (See Appendix 2.2 for more information)
    DWORD    Unknown (always 0xc772bf98)
    ...
    ...     # Same as Prebuilt Network Subfile structure
    ...
    INT64   Demolishing costs (see Appendix 2.10)
    BYTE×21 Unknown (apparently always 0x00)
    BYTE    Unknown (always 0x01)
    DWORD   Opposing tunnel portal memory address
    DWORD   Opposing tunnel portal subfile TID (0x8a4bd52b)

# Network Manager Subfile (0xc990bd46)

## Structure

    DWORD    Size
    DWORD    CRC
    DWORD    Memory
    WORD     Version (always 1)
    DWORD    Count of pointers to follow
        DWORD    Memory address
        DWORD    Type ID, seen 0x49c1a034, 0x8a4bd52b, 0x49cc1bcd (prebuilt network, tunnels, bridges)
