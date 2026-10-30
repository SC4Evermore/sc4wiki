---
title: "Network Specs/Individual Network RULs"
description: ""
published: false
date: '2019-08-04T05:45:29Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-12T20:46:09Z'
---

This file contains information related to the individual Network [RULs](/rul).

## Network Specific RULs

Each individual network, including water pipes (but not power poles), has two RUL files. One is the main RUL file for a given network, while the other is a supplementary RUL for a given network. RULs ending in odd values are the main network-specific RUL. While RULs ending in even values are the supplementary RUL for a given network. This covers RUL files from (address) *0x0A5BCF4B/AA5BCF57/00000001* to *0x0A5BCF4B/AA5BCF57/00000018*.

## Format

<!-- unconverted template: TTC -->

<!-- unconverted template: colour --> -This basically contains <!-- unconverted template: colour --> here name. The engine recognises the different names used in the header section here, and does have an impact/influence on the network tool(s) used. A typical sample portion of RUL code for individual networks may look something like the following (this was taken from a Highway RUL file):

<!-- unconverted template: TTC -->

Version/Type: Value1/Value2/Value3

Different Versions/Types have different number of Values following after them, with differing purposes.

Format is broken up into parts below, and is as follows.

### For Type 1 Lines

<!-- unconverted template: TTC --> 1\[Type\],West,North,East,South

West/North/East/South use the following CheckFlag values:

`00 - no connection`  
`01 - sloped connection-to the left`  
`02 - straight connection`  
`03 - sloped connection-to the right`  
`04 - shared median`  
`11 - sloped connection from an intersection - to the left`  
`13 - sloped connection from an intersection - to the right`

There is quite a lot more number designations for some of the more complex stuff (such as Rail). The above ones are just the basic types that cover and work with most networks.

<!-- unconverted template: also -->

### For Type 2 Lines

<!-- unconverted template: TTC --> 2\[Type\],X,W,N,E,S

X = See table further below.

WNES = West/North/East/South - uses the same CheckFlag values as above. "?" (without quotes) is also valid though for Type2 lines as a wildcard.

### For Type 3 Lines

<!-- unconverted template: TTC --> 3\[Type\],X,FSH/Path/ExemplarReference,Rotation,Flip

X = See table further below.

Rotation: 0-3. Rotate piece:

`0=No change`  
`1=90 Degrees right`  
`2=180 Degrees`  
`3=270 degrees right/-90 degrees left.`

Where an Exemplar exists for the reference, the Exemplar subsequently points to a S3D file (NOTE: Referenced Exemplar files follow a specific GroupID format, for the different network types).

### Table for Type2 and Type3 Lines

X = Reference in relation to the tile being referenced. For Type3 lines, zero is also valid reference and denotes that the image being loaded into the tile. The same also applies to other (non-zero neighbouring) tiles as well. Zero is the centre point, or the primary tile being coded for for the Type1 line, to which all other tiles are referenced in relation to.

Each box/number here represents an in-game tile.

<figure>
<img src="/_files/images/nsinr1.jpg" title="NSINR1.jpg" />
<figcaption>NSINR1.jpg</figcaption>
</figure>

### Further explanation of CheckFlags

<figure>
<img src="/_files/images/nsinr2.jpg" title="NSINR2.jpg" />
<figcaption>NSINR2.jpg</figcaption>
</figure>

#### Setup

Imagine yourself at the centre of this transit tile at point E, looking North to point 2. Segment AB is the side for which we are trying to determine the border type.

#### Explanation

The RUL entries dictate the centre point of the network (in this case, roads) along segment AB, and the direction the network is going, in comparison to segment E2. If the vector of the transportation tile is parallel with EA, the angle would be -45° in comparison to E2. Likewise, if the vector of the transportation tile is parallel to EB, the angle would be +45° in comparison to E2.

#### Table

The Pixel position is based on the 128 pixel wide zoom 5 textures, with pixel points 0-127. Also, the pixel values might be off slightly due to anti-aliasing in the textures.

The simpler table, showing absolute positions only:

<figure>
<img src="/_files/images/nsinr3.jpg" title="NSINR3.jpg" />
<figcaption>NSINR3.jpg</figcaption>
</figure>

The more complex table, showing the relative offsets as well as absolute positions:

<figure>
<img src="/_files/images/nsinr4.jpg" title="NSINR4.jpg" />
<figcaption>NSINR4.jpg</figcaption>
</figure>

That about covers it. As mentioned, there are more RUL designations than just those mentioned here. Most other RUL designations though are more complex. For this reason it’s advised to try and grasp the concepts of the above items first.
