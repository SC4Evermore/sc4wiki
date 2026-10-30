---
title: "Bridges"
description: ""
published: false
date: '2019-08-04T06:00:26Z'
tags: ["Transit Modding", "NAM", "Custom Content", "Network Elements"]
editor: markdown
dateCreated: '2008-07-29T07:16:59Z'
---

Bridges are a subset of [Transit Networks](/transit-network) and apply mainly to vehicular travel. Technically power lines can form a bridge (the model switches to show the yellow orbs) but for the present purposes of this article, only networks which move [Sims](/sims) will be discussed. They are used by the game to traverse bodies of water, or even land if the bridge is high enough. All of the standard game transit networks, with the exception of Streets and One-Way Roads can create bridges. With developments in the [NAM](/nam), it is now possible to create bridges for any transit network that is contained in the Bridge Controller file in the NAM.

## Types of Bridges

### Standard Game

*Bridges listed in alphabetical order by name.* <!-- unconverted template: head --> <!-- unconverted template: row --> <!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --><!-- unconverted template: row --> \|}

### Custom Made

*Listed Alphabetically by name*

#### Road

- Covered Wooden Bridge - threestooges
- CSX Bridge - Kwanyoni - Colyn
- Dusktrooper Road Bridge - DuskTrooper
- Garabit Viaduct - paulvmontfort
- Garabit Viaduct Green Version - Modelled: paulvmontfort; Modded: Jeronij
- Krummbach Bridge (Road Version) - Jeronij
- Old Road Bridge - Jeronij

#### Street

- Rural Street and Rail Bridge - Jeronij

#### Rail

- Metal Arch Rail Bridge - Fukuda
- Metal Pylon Rail Bridge - Fukuda
- Modern Rail Bridge - Jeronij
- Rural Street and Rail Bridge - Jeronij
- Warzone Bridge - Jeronij

#### Avenue

- Millau Viaduct - Fukuda
- Plain Avenue Bridge - Tropod

#### One-Way Road

- Plain One-Way Road Bridge - Tropod

#### Highway

- Akashi-Kaikyo Bridge - Fukuda
- Tsing Ma Bridge (Hong Kong) Single Deck - Jeronij

#### RealHighway Mod ([RHW](/rhw))

- Plain RHW-2 Bridge - smoncrie
- Plain RHW-4 Bridge - smoncrie
- Steel Arch RHW-4 Bridge - smoncrie

#### Elevated Rail/GLR

#### Monorail

#### High Speed Rail

- GHSR by Jeronij
- HSR Bridge by Jeronij

## Modelling

> Main article: [Tutorial:Bridge Modeling](/tutorial/bridge-modeling)

A bridge is essentially composed of three pieces:

- A Start/End Piece (automatically reversed when drawn in game)
- A Support Piece (is what extends to the surface to support the bridge)
- A Repeat Piece (fills in the gaps between the Start/End and Support pieces)

Each bridge piece can be modelled in the [BAT](/bat) and must be rendered with a specific and unique ID. The [Model Exemplar](/model-exemplar) that is attached to the model will define what type of bridge it will be used with. A tutorial for the creation of basic, three piece bridges can be found at [SC4Devotion](http://sc4devotion.com/forums/index.php?topic=930.0). The creation of more complex bridges, like suspension bridges, involves the use of [RULs](/rul).

The [LODs](/lod) for the bridge may be as wide as necessary, but may only be 16m (one game tile) long. They should be rendered with xy coordinates of 0,0. If the [LOD](/lod) covers the roadbed, it will obscure the vehicles using the bridge so care must be taken when designing bridges with parts above the roadbed. A bridge that wishes to include sections longer than 16m must break the section into 16m segments. For example: if you have a Start/End piece that is 32m long, it must be rendered as two separate 16m long models, each with its own ID. They will then be modded as Start/End pieces in the [Reader](/reader).

Hint: A bridge can be built, carry commuters, and still not be visible. This would indicate a GroupID and/or InstanceID problem with the files involved, and/or possibly a S3D file problem.

## Modding

To Be Written

> **Note:** This article needs expanding.
