---
title: "Network Flags"
description: ""
published: true
date: '2023-01-29T11:00:35Z'
tags: ["Transit Modding"]
editor: markdown
dateCreated: '2011-10-05T06:29:23Z'
---

**Network Flags** are used in [RUL 0x10000000](/rul-0x10000000) (RUL0), [RUL 0x10000001](/rul-0x10000001) (RUL1) and the [Individual Network RULs](/individual-network-ruls) to signify network layouts. Their format is different for each of these files.

They are entered in the *0xSSEENNWW* syntax with two digits per direction for RUL0 and RUL1 files. They are entered as one- or two-digit numbers in *W,N,E,S* format for the Individual Network RULs. When used in the Individual Network RULs, you can omit the leading zero (if present) from the Network Flag (i.e. *04* is simply *4*).

## Values

Known acceptable values, when viewed with the bottom being the side modified, are:

- 00 - No connection.
- 01 - Left at 45 degree angle (diagonal connection).
- 02 - Straight connection.
- 03 - Right at 45 degree angle (diagonal connection).
- 04 - Shared median for 2 tile wide networks.

The Individual Network RULs have additional flags available, such as:

- 11 - Off center "blend" sloped connection for left angled 1 becoming straight 2.
- 13 - Off center "blend" sloped connection for right angled 3 becoming straight 2.

Rail-type networks also use several higher flags:

- 21 - Diagonal switch left
- 23 - Diagonal switch right
- 22 - Secondary orthogonal blend-switch left
- 42 - Secondary orthogonal blend-switch right
- 32 - Orthogonal-diagonal switch cross-over left
- 52 - Orthogonal-diagonal switch cross-over right
- 62 - Wye
- 72 - W-switch

## Further Explanation

Take, for example, the image below, representing a tile, with the corners labeled with letters and the sides labeled with numbers. Point *E* marks the center of the tile. Assume that Side *AB* is "North" for purposes of this example, remembering that the values in [RUL](/rul) files are given for the North, East, South, and West sides of the tile.

<figure>
<img src="/_files/images/nsinr2.jpg" title="NSINR2.jpg" />
<figcaption>NSINR2.jpg</figcaption>
</figure>

Suppose Side *AB* is the side of the tile for which we are trying to determine the Network Flag. This would be the "North" side of the tile in our example for the purposes of inputting the value into a RUL file. Given such a tile, the game needs to know the vector (direction) the network travels across the tile, and it defines this direction by defining a vector from Point *E* to some point along Side *AB* that is a parallel vector to the actual vector of the network across the tile. Once this parallel vector is defined, it is matched up to the corresponding Network Flag, which is then input into the RUL file.

Graphically, one could determine the parallel vector by first tracing the direction the network travels across the tile, and then drawing a straight vector passing through Point *E* that is parallel to the direction of the network.

If the parallel vector, starting at Point *E*, crosses Side *AB* of the tile at Point *2*, tracing the line *E2* across the tile, then it would be a straight connection, and the appropriate flag for Side *AB* (the "North" side in this example) would be *02*. If instead the parallel vector travels at a left diagonal from Point *E* and crosses the edge of the tile at Point *A*, then it would be a diagonal 45 degree left connection, and the appropriate Network Flag would be *01*. If the parallel vector does not cross Side *AB* of the tile at all, then the Network Flag would be *00*, for no connection.

One would also need to then determine where this same parallel vector through Point *E* crosses the other three sides of the tile, and assign the appropriate Network Flags to each side, remembering of course that the direction is defined relative to a new point for each side of the tile. For example, while Line *E2* was straight (Flag *02*) for the "North" side of the tile, Line *E1* would be straight (Flag *02*) for the "West" side of the tile. The four Network Flags would then be input in to the RUL file in the appropriate format.

### Pixel Table

The point where the parallel vector crosses Side *AB* of the above example can also be measured as the corresponding pixel along that edge of the tile texture. The following tables show you, for a tile defined as above with a road running across it, the corresponding Network Flags for various pixel positions. The pixel positions are given for where the left edge, centerline, and right edge of the network cross the edge of the tile.

The following pixel position is based on the 128 pixel wide zoom 5 textures, with pixel points 0-127. Also, the pixel values might be off slightly due to anti-aliasing in the textures.

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

## Game View Tips

Remember that "to the right" and "to the left" are relative to the tile edge with the camera facing perpendicular to the tile edge. Consequently, as you rotate the camera, you have to keep in mind what direction you are trying to define.

A little guide to convert from edge-view to screen-view:

If your camera is facing (x-Direction, below), and you are defining the Network Flag for the "North" side of the tile,

- North: 01 is to the left, 03 is to the right.
- East: 01 is up, 03 is down.
- South: 01 is to the right, 03 is to the left.
- West: 01 is down, 03 is up.

1.  [Network Specs](/network-specs)
