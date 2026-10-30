---
title: "Individual Network RULs"
description: ""
published: false
date: '2021-05-20T10:14:25Z'
tags: ["NAM", "Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2009-01-25T05:03:59Z'
---

**Individual Network RULs** are [RUL](/rul) files that deal exclusively with one network, covering the basic placement and single-network intersections. Each network has two separate RUL files: a basic RUL file that covers basic placement, and an advanced RUL file that handles more complicated setups. Intersections involving multiple network types are handled by the [Multi-Network RUL Files](/rul-file#multi-network-rul-files).

## List of Files

All of the Individual Network RUL files are listed below, by [Instance ID](/instance-id). All of them have [Type ID](/type-id) *0x0A5BCF4B* and [Group ID](/group-id) *0xAA5BCF57*. These RUL files cover all of the transit networks, as well as water pipes. They do not, however, cover power lines. Note that it is not possible to create new Individual Network RUL files, however these files may be modified.

- 0x0000001 - Elevated Highway Basic RUL
- 0x0000002 - Elevated Highway Advanced RUL
- 0x0000003 - Pipe Basic RUL
- 0x0000004 - Pipe Advanced RUL
- 0x0000005 - Rail Basic RUL
- 0x0000006 - Rail Advanced RUL
- 0x0000007 - Road Basic RUL
- 0x0000008 - Road Advanced RUL
- 0x0000009 - Street Basic RUL
- 0x000000A - Street Advanced RUL
- 0x000000B - Subway Basic RUL
- 0x000000C - Subway Advanced RUL
- 0x000000D - Avenue Basic RUL
- 0x000000E - Avenue Advanced RUL
- 0x000000F - Elevated Rail Basic RUL
- 0x0000010 - Elevated Rail Advanced RUL
- 0x0000011 - One-Way Road Basic RUL
- 0x0000012 - One-Way Road Advanced RUL
- 0x0000013 - [RHW](/rhw) ("Dirt Road") Basic RUL
- 0x0000014 - [RHW](/rhw) ("Dirt Road") Advanced RUL
- 0x0000015 - Monorail Basic RUL
- 0x0000016 - Monorail Advanced RUL
- 0x0000017 - Ground Highway Basic RUL
- 0x0000018 - Ground Highway Advanced RUL

Changing the Subway RULs will either cause a CTD when you start the game, or not make any changes, the same is probably true for Pipe RULs. There are hints that Subway RULs are located inside the EXE, especially as the straight open top subway section is not handled by any of the RUL Files.

## Format

The Individual Network RUL Files all have the same format, which is unique to this type of RUL file. The general layout consists of a header, followed by repeating blocks of data that contain the actual rules for that network type.

### Header

Each file begins with the header on the first line. There is only one header per file, and it can come in two formats. The game engine recognizes the different names used in the header section, and the header does have an impact/influence on the network tool(s) used.

The first type of header looks like:

`#(transittype)Rules#`

The second type of header looks like:

`#Transmogrify`

A *\#Transmogrify* header can be used in order to automate the rules rotations and flips where applicable. It will take the supplied rule and rotate/flip it for all directions. However, in special cases such as designing turning lanes, this produces improper results in viewing. For those interested, Transmogrify means to change something with weird and often humorous results.

Common examples of headers are:

`#HighwayRules#`  
  
`#RoadRules#`  
  
`#RailRules#`

### Comments

These files support comments, which are simply lines preceded by a semicolon. In some instances it is simply a single line, in others a blank comment line is used both before and after the comment line itself, for example:

`;`  
`;Comment or description`  
`;`

Typically, the comment simply describes the block(s) that follow the comment.

### RUL Blocks

**RUL Blocks** consist of some combination of **Type 1**, **Type 2**, and/or **Type 3** Lines. These types are so named because each line begins with either a 1, 2, or 3. Each block begins with a Type 1 Line, and may be followed by several Type 2 Lines, which are then followed by a Type 3 Line for each Type 1 or Type 2 Line. The Type 1 Line defines the central tile of the rule pattern, while the Type 2 Lines (if present) define tiles adjacent to the central tile. Type 3 Lines define additional information about each of the tiles involved in the rule. Together, each block of lines consist of the complete rule. For example:

`Type 1`  
`Type 3`

is a valid RUL block.

`Type 1`  
`Type 2`  
`Type 2`  
`Type 2`  
`Type 3`  
`Type 3`  
`Type 3`  
`Type 3`

is also a valid RUL block.

#### Type 1 Lines

**Type 1 Lines** are lines that describe the basic boundaries of the central tile. The format is:

`1,W,N,E,S (i.e. 1,13,2,0,2)`

The first value, "1", defines the line as Type 1.

*W,N,E,S* are unique [Network Flags](/network-flags) that must match the value of the tile next to it (i.e. a 2 touches a 2). Each of these four values corresponds to a specific side of the tile, namely West, North, East, and South. Known acceptable values are:

- 0 - No connection.
- 1 - Left at 45 degree angle.
- 2 - Straight connection.
- 3 - Right at 45 degree angle.
- 4 - Shared median for 2 tile wide networks.
- 11 - Off center "blend" sloped connection for left angled 1 becoming straight 2.
- 13 - Off center "blend" sloped connection for right angled 3 becoming straight 2.

While these are the most common Network Flag values, they are not the only ones used. Rail networks in particular will use other values than those listed above. A more in depth explanation is offered [here](/network-flags).

If one draws a little text art for the values shown in the format above, one gets:

    +-----+
    |  2  |
    |13  0|
    |  2  |
    +-----+

#### Type 2 Lines

**Type 2 Lines** describe the squares that must be adjacent to the tile defined in the Type 1 line for this RUL Block to be valid. Their format is:

`2,X,W,N,E,S`

The first value, "2", defines the line as Type 2.

The "X" value describes the relationship of this "limiting tile" in relationship to the reference (central) tile. There are 24 possible values for *X* using the following convention:

    1 - West
    2 - Northwest
    3 - North
    4 - Northeast
    5 - East
    6 - Southeast
    7 - South
    8 - Southwest
    9 - West 2 tiles from center
    10 - West-northwest 2 tiles from center
    ...
    24 - West-southwest 2 tiles from center

These values are illustrated in the table below, where "0" is the central (reference) tile defined in the Type 1 Line:

<figure>
<img src="/images/NSINR1.jpg" title="NSINR1.jpg" />
<figcaption>NSINR1.jpg</figcaption>
</figure>

W,N,E,S are [Network Flags](/network-flags) that follow the same convention as used in Type 1 Lines.

So, expanding on the example used above for a Type 1 line, if that line was followed by the following three Type 2 lines:

`2,1,0,1,13,0`  
`2,6,13,0,0,1`  
`2,7,0,2,13,2`

These three tiles would have to be adjacent to our reference (Type 1) tile for this "rule" to be valid.

The little text art picture looks like:

    +-----+-----+
    |  1  |  2  |
    |0  13|13  0|
    |  0  |  2  |
    +-----+-----+-----+
          |  2  |  0  |
          |0  13|13  0|
          |  2  |  1  |
          +-----+-----+

Notice how the sides line up nicely.

#### Type 3 Lines

**Type 3 Lines** state what [FSH](/fsh) images to load into which tiles and if any manipulation is needs to be done to the image before it is placed, such as rotating or flipping the image. Basically these manipulations are responsible for making sure curves work, as well as highways that often take up 2 tiles. They have the following format:

`3,Y,FSH,ROTATE,FLIP`

The first value, "3", defines the line as Type 3. The attributes that follow are:

- *Y* - Works just like *X* from the Type 2 lines, with the exception that zero (0) is now a valid field. A "0" value denotes that this particular Type 3 line is defining the image for the central reference (Type 1) tile. Otherwise, the value here will match that of the corresponding Type 2 line.
- FSH - This value points to the [Instance ID](/instance-id) of a [FSH](/fsh) [texture](/texture) that will be used for the tile in question. It can also point to an [exemplar](/exemplar) IID for this network type.
- ROTATE - Rotation to be applied to the image before it is placed in game, if any. This standard specifies the rotation of the tile as well. Valid values are 0-3 with each increment being a 90 degree clockwise turn, see below.
- FLIP - Flip the texture horizontally and vertically like a mirror image, however retain the rotation in-game of the piece in question. This helps to cut down on the textures needed. Values are 0 and 1 - False and True.

Rotation values are as follows:

`0 = No change`  
`1 = 90 Degrees right`  
`2 = 180 Degrees`  
`3 = 270 Degrees right/-90 degrees left.`

Changing this value defines what angle the tile is being viewed from in game in the most basic sense. For example, a value of "1" indicates that during standard conditions, the tile would be rotated 90 degrees right from the straight ahead viewing angle.

Where an Exemplar is referenced instead of a FSH file, the Exemplar subsequently points to a S3D file. Note that referenced Exemplar files follow a specific [Group ID](/group-id) format, for the different network types.

1.  [Network Specs](/network-specs)
