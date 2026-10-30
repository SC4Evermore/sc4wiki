---
title: "Puzzle Piece"
description: ""
published: false
date: '2019-08-04T05:46:34Z'
tags: ["Transit Networks", "Transit Modding"]
editor: markdown
dateCreated: '2008-06-03T05:14:54Z'
---

A **Puzzle Piece** is a ploppable, fully-functioning [Transit Network](/transit-network) piece, sometimes also known by the more technical term, **Interchange-base Related Item (IRI)**. Puzzle Pieces can be placed into "TAB Loops", known as **Rotation Rings**, allowing multiple items to be placed under a single menu button. All puzzle pieces are technically 3-dimensional objects, subject to the guidelines of [Transit Modelling](/tutorial/modelling-for-networks). They are defined in [RUL 0x10000000](/rul-0x10000000).

In addition to those contained in the [Network Addon Mod](/network-addon-mod), all Maxis Interchanges are technically Puzzle Pieces.

Essentially, Puzzle Pieces are generally used to make items that would not be possible simply through draggable means possible. As [Override Networks](/override-network) have advanced, some items previously confined to Puzzle Piece implementations (such as Ground Light Rail) have been made draggable.

## Puzzle Pieces and Transit-Enabled Lots

The term Puzzle Piece is sometimes mistakenly used to describe [Transit Enabled Lots](/transit-enabled-lots). The difference between the two is that a Puzzle Piece is considered to be simply a ploppable extension of a draggable [Transit Network](/transit-network). Transit-Enabled Lots, or TE Lots, are simply Lots which have been made to look like network pieces, but actually have no actual network functionality, and are generally intended only for [Transit Switches](/transit-switches) or [Toll Booths](/toll-booths). The [Traffic DataView](/traffic-dataview) shows TE Lots as "blank spots" in the middle of the map, whereas Puzzle Pieces appear as normal networks.

In addition, there are some game stability issues involving the interaction of Puzzle Pieces with TE Lots, in that hovering Puzzle Pieces over TE Lots of the same network (or sometimes vice-versa) often causes [CTDs](/ctd).

## Creating Puzzle Pieces

There are six things which are needed in order for a Puzzle Piece to function:

- Entries in [RUL 0x10000000](/rul-0x10000000)
- 1 S3D tile for each segment of the Puzzle Piece, according to [Transit Modeling](/transit-modeling) guidelines
- 1 SC4Path for each segment of the Puzzle Piece
- 1 Puzzle Piece Exemplar for each segment of the Puzzle Piece
- 1 Preview Model, consisting of all segments combined into a single model
- 1 Effects Directory File for linking the Preview Model to RUL 0x10000000

Textures on S3D tiles appear lighter than on the 2D networks, so when making puzzle pieces for these (such as the Road wide Curves) you need to darken them, this can be done in the GIMP and a formula to try first is: -22 brightness, -6 hue. But with different textures this formula can be different, and the only way to get it prefect is through trial and error.

More information on creating puzzle pieces can be found in [this tutorial](/tutorial/creating-puzzle-pieces).
