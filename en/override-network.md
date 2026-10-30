---
title: "Override Network"
description: ""
published: true
date: '2019-08-04T06:00:50Z'
tags: ["NAM", "Transit Modding"]
editor: markdown
dateCreated: '2008-07-27T14:15:35Z'
---

An **Override Network** is an emulated new network, produced by using overrides in [RUL 0x10000002](/rul-0x10000002) on existing draggable in-game [Transit Networks](/transit-network). The in-game network is kept intact, as the Override Network is triggered by doing something unusual with the network beyond its normal usage, like drawing some sort of little-used setup, or using a starter piece. Examples of Override Networks include the 4-lane Rural Highway (RHW-4) in the [RealHighway](/realhighway) Mod (RHW) and the "Texture Variations" in the [Street Addon Mod](/street-addon-mod) (SAM).

The concept was first explored by [Teirusu](/people/teirusu) of the [NAM Team](/nam-team) (then Modd Squad), who created "short-range" overrides with the NAM Road Turning Lanes and the Roundabout Plugins. [qurlix](/people/qurlix) built on these ideas to create the RHW-4 network as part of the initial Version 12 release of the RHW (then called the Rural Highway Mod) in 2005. Today, it is one of the most heavily utilized techniques in transit modding.

There are a few ways that Override Networks are initiated. The first of these is the **Side-by-Side Override**. A Side-by-Side Override (**SBSO**) initiates an Override Network by specifying that Network A, alongside either Network A or Network B, initiates Network C, an Override Network. This method was used to initiate the RHW-4 in the RHW mod, until it was changed in January 2008 as part of Version 20.

The next type of trigger is the **Puzzle Drag Override** (**PDO**), also sometimes known as a **Starter Piece Override**. A PDO utilizes a [False Intersection](/false-intersection) between two different networks, difficult or impossible to draw using the networks as intended, assigning it to the orthogonal or diagonal texture of the override network using [RUL 0x10000001](/rul-0x10000001). Since this false intersection cannot be drawn, it must be placed using a special starter piece. The technique was developed by [smoncrie](/people/smoncrie), and first implemented by [memo](/people/memo) with Draggable GLR in the June 2007 NAM. It was also utilized as part of the Street Addon Mod by [jplumbley](/people/jplumbley), and the RHW-4 was converted to it with the Version 20 release. The "puzzle drag stubs" that are used at the ends of pieces to initiate these overrides can be attached to any other sort of puzzle piece. A prime example of this is the Ramp Interface pieces in the RHW.

There is also another type of intersection-based override, known as a **Lengthwise Override** (**LWO**), which is less common, and generally used over short range. It implements an override based on a normally draggable setup. Primary examples of LWO include the Road Turning Lanes (both the current and future versions) and the Avenue Turning Lanes.

In some instances, these types of overrides can be combined to create Hybrid Overrides. A prime example of this is the RHW-8S network in the RHW mod, which initiates a Side-by-Side Override on two Puzzle Drag Overrides.

### Related Topics

- [High Speed Rail Project](/high-speed-rail-project)
- [Network Addon Mod](/network-addon-mod)
- [Network Widening Mod](/network-widening-mod)
- [RUL 0x10000000](/rul-0x10000000)
- [RUL 0x10000001](/rul-0x10000001)
- [RUL 0x10000002](/rul-0x10000002)
- [RealHighway Mod](/realhighway)
- [Street Addon Mod](/street-addon-mod)

> **Note:** This article needs expanding.
