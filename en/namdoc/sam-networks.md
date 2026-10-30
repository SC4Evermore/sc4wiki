---
title: "SAM Networks"
description: ""
published: false
date: '2019-08-04T22:57:14Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2018-01-09T05:11:18Z'
---

## SAM Networks

Each override network is initiated by first placing the appropriate Starter Piece (all SAM Starter Pieces are found under the Street Addon Mod button on the Roads menu), and then dragging the Street network through the Starter Piece. This process is shown below.

<figure>
<img src="/images/sam-starter.jpg" title="sam-starter.jpg" />
<figcaption>sam-starter.jpg</figcaption>
</figure>

## Constructing Diagonals and Curves

With the exception of SAM 1, the Parking Lots set, all SAM networks can go diagonal, with SAM overrides continuing through the NAM's Diagonal Street Plugin, provided one is using either the FLEX/Helper Pieces or the Draggable Method. (The Diagonal Street Fillers, as static puzzle pieces, cannot carry overrides.) The process is shown below.

<figure>
<img src="/images/sam-diagonal.jpg" title="sam-diagonal.jpg" />
<figcaption>sam-diagonal.jpg</figcaption>
</figure>

All SAM Sets, with the exception of SAM 1, can also override the NAM's Draggable Wide-Radius Curves for the Street network, simply by dragging the SAM network up to the edge of the curve, or drawing the pattern while continuing a SAM override. This process is shown below:

<figure>
<img src="/images/sam-wrc.jpg" title="sam-wrc.jpg" />
<figcaption>sam-wrc.jpg</figcaption>
</figure>

For quick reference, the patterns for the Draggable Wide-Radius Curves for the Street network are shown below:

***Unfinished: Add link (not existing yet) to Street Wide-Radius Curve Patterns***

All networks, including SAM 1, also support the default sharp 90° bend.

(Older, static puzzle piece curves for some SAM sets can also be found in the [Rural Roads Mod](/rural-roads-mod) (RuRP), and will be found under the Rural Roads button on the Roads menu.)

## Intersecting and Transitioning to Other Networks

### Intersecting and Transitioning to Other Networks

With supported networks--including Roads, One-Way Roads, Avenues, and Rails (including all Rail-based override networks\*)--intersections and crossings can simply be built by dragging the overridden Street network through the network, just as one would with any other draggable network. Supported networks allow for crossings in all possible permutations of orthogonal and diagonal networks. (The [High Speed Rail](/high-speed-rail) override network also allows orthogonal x orthogonal crossings of select SAM networks via static puzzle pieces.)

<figure>
<img src="/images/sam-intersection.jpg" title="sam-intersection.jpg" />
<figcaption>sam-intersection.jpg</figcaption>
</figure>

In addition, it is possible to transition to the Road, One-Way Road, or Avenue network by simply dragging to connect one of these networks to the SAM Network.

SAM Set 1 (the Parking Lots) are a special case. They can intersect or transition to other networks in a clean visual manner due to how they dovetail with the base Street network, but technically cannot form intersections or transitions. The overrides will not continue beyond the intersection, unlike what occurs with all the other SAM networks.

### SAM Interaction with the Street Network

SAM Overrides are pervasive. The presence of a SAM Starter Piece will cause all Streets with exposure to the SAM Street--including those that intersect it--to also be overridden. As such, it is not possible to create an intersection between a SAM Street and a Maxis Street, or between two different SAM types. SAM Override Behavior on Street Network

<figure>
<img src="/images/sam-override.jpg" title="sam-override.jpg" />
<figcaption>sam-override.jpg</figcaption>
</figure>

Transitions between two SAM Sets can be approximated by placing two different Starter Pieces back to back, or by quickly transitioning from SAM -\> Road -\> Street, which breaks the override, though care should be taken even in these cases. Attempting to drag two SAM Sets into one another will simply result in a "tug-of-war" between the two sets, which can have unpredictable and unstable results.

- (Rail-based override networks include [Single Track Rail](/single-track-rail) (STR) in both Maxis Rail and [RealRailway](/realrailway) (RRW) forms, plus the L1 and L2 Draggable Elevated RealRailway Viaducts.)

## Bridges

Select SAM sets include bridge support. To access the SAM's bridge options, one should simply drag the Street network across the body of water (or deep canyon) wishes to cross, at which point the SAM bridges will show up among the Street options.

## Tunnels

The base Street network **does NOT support tunnels**, and accordingly, neither do any of the SAM's Street-based override networks. While certain slope settings may permit a tunnel to appear, it will be completely non-functional, due to hardcoded limitations that prevent traffic from using it. There is no known solution to this limitation at present. The only possible workaround at present is to transition to another network that does support tunnels.

## Known Issues

- Attempting to intersect a SAM override network with another NAM override network that does not support SAM crossings may de-stabilize both overrides, causing them to alternate which override is broken with clickaround.
- Attempting to intersect two SAM types, or transition directly between them will cause override instability.
- Attempting to build multiple Draggable Wide-Radius Curves and/or intersections directly adjacent to one another may break SAM overrides, causing reversion to Street.
