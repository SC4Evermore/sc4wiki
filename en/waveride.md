---
title: "WAVERide"
description: ""
published: false
date: '2019-08-04T05:43:10Z'
tags: ["Transit Modding"]
editor: markdown
dateCreated: '2011-06-01T06:10:51Z'
---

**WAVERide** (also referred to as **FLEX** items) is a term coined by [Blue Lightning](/people/blue-lightning) of the [NAM Team](/nam-team) to refer to items which blur the line between [Puzzle Pieces](/puzzle-pieces) and [Override Networks](/override-network), allowing for the modularity and flexibility of an override with a more complicated setup that is near-impossible or completely impossible through standard dragging and network override techniques.

Technically, the first WAVERide pieces were the Diagonal Street Helper Pieces, introduced by [memo](/people/memo) in NAM Version 20 from December 2006. These pieces got around the limitations of the existing "zig-zag" draggable override, allowing diagonal streets over shorter stretches, slope tolerance, and most importantly, intersection capability with other networks.

The technology found its way into the [RealHighway](/realhighway) (RHW) mod in 2010, when Blue Lightning created the **FLEXFly** (*Flex*ible *Fly*over) system as part of the Version 4.0 release, which allowed for single-lane flyover ramps, under which RealHighway networks could pass in various configurations. The popularity of FLEXFly has often led to any sort of WAVERide being called a "Flex" setup. The Version 4.2 release of RealHighway will include a new WAVERide setup developed by [Tarkus](/people/tarkus), FlexSPUI, which allows the construction of a flexible, modular Single-Point Urban Interchange (SPUI) in various configurations.

The various starter pieces for override networks are Flex pieces.

### Flex modding specs

Technically, a Flex piece is a puzzle piece that places an intersection that is impossible to drag with the normal network tools (see RUL0; the intersection is defined by the CheckTypes).

For instance:

    CheckType = a - rail: 0x04000404 dirtroad: 0x02000200, 0xFFFFFFFF optional

This intersection is defined in RUL1 and assigned a network tile.

Following the above example, in the \[RailDirtRoadIntersectionSolutions\]:

    TYPE1=0x04000404,0x02000200,0x5d6f0000,0,0

Finally, this network tile can be the start of an override defined in RUL2.

    0x5d6f0000,1,0,0x5f33fc00,0,0=0x5d6f0000,1,0,0x5d640000,1,0

The above example is how the draggable rail viaducts are started.
