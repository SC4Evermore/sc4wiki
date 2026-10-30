---
title: "Network Widening Mod"
description: ""
published: false
date: '2019-08-10T08:44:39Z'
tags: ["NAM/project"]
editor: markdown
dateCreated: '2008-07-27T14:10:23Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Network Widening Mod</th></tr>
<tr><td><strong>Name</strong></td><td>Network Widening Mod (NWM)</td></tr>
<tr><td><strong>Status</strong></td><td>Released <br></td></tr>
<tr><td><strong>Version</strong></td><td>Included in <a href="/nam">NAM</a></td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="/plugin/nwm">NWM Plugin</a></td></tr>
</table>
</div>

<img src="/_files/images/owr3.jpg" title="The OWR-3 as it appeared in an initial Orthogonal Prototype in 2008" width="400" alt="The OWR-3 as it appeared in an initial Orthogonal Prototype in 2008" /> The **Network Widening Mod** (**NWM**) is a transit mod produced by the [NAM Team](/nam/members), consisting of a series of [Override Networks](/override-network), which are wider variants of the existing in-game networks, extending the [RHW](/rhw) concept to Car-Based Surface Networks. Since the switch to the "Monolithic NAM" paradigm for the March [2013](/2013) release of NAM Version 31.0, the NWM is now included as an option in the full NAM package.

## History

The Network Widening Mod was initially conceived in December 2006 by [jplumbley](/people/jplumbley), [Tarkus](/people/tarkus), [Ryan B.](/people/ryan-b) and [beskhu3epnm](/people/beskhu3epnm). Upon seeing Tarkus' efforts reviving the [RealHighway](/realhighway) project (RHW, which then stood for "Rural Highway"), jplumbley contacted him to discuss the underlying techniques behind the RHW, as he had an interest in seeing wider One-Way Roads come to fruition, with texture work by his [NHP](/nhp) colleague beskhu3epnm. About a year beforehand, Ryan B. had released a cosmetic mod known as the "Two-Way Left Turn Lane Mod" or TWLTL, which restriped the game's default Avenue network to have a center left turn lane, which had also intrigued the NWM founders, who saw the potential to not only make the TWLTL co-exist with the standard Avenue, but to make the center turn lane functional. Shortly after the initial discussion to this effect, Tarkus worked up an initial prototype of the 5-lane Turning Lane Avenue (TLA-5). jplumbley also worked up an initial prototype of the 5-lane One-Way Road (OWR-5), and Tarkus began to experiment with networks wider than two tiles, first showcasing a prototype of a 7-lane Turning Lane Avenue in 2007.

The project was on hiatus for an extended period of time through much of 2007 and 2008, in large part due to the interference that the NAM's existing Road Turning Lanes Plugin and One-Way Arrow Reduction Plugin presented to override initiation at intersections. In the meanwhile, some ideas Tarkus and jplumbley had for the project made their way to the RHW and brand-new [Street Addon Mod](/street-addon-mod) (SAM), respectively, and jplumbley's focus eventually shifted toward the [Traffic Plugin](/traffic-plugin).

The lengthy dormancy of the NWM put the future of the project in doubt for a considerable period of time. However, development recommenced privately in 2009 with [superhands](/people/superhands) from the [Railway Addon Mod](/railway-addon-mod) development tteam coming on board to collaborate with Tarkus. The results of their efforts were first displayed in a re-opened NWM development thread at [SC4 Devotion](/sc4-devotion) in March 2010. Finally, after a 3 1/2 year development cycle, NWM Version 1.0 was released on May 9, [2010](/2010), coinciding with the release of NAM 28.

The breakthrough discovery of [Distilled Intersection Paths](/distilled-intersection-paths) shortly after that, based on some earlier traffic simulation research that Tarkus and jplumbley had done, allowed for functional differentiation of some of the wider single-tile networks, as well as the dual-tile 6-lane Road network (RD-6), prompting the release of NWM 1.1 as part of the NAM 29 cycle in August [2010](/2010). Version 2.0, released on September 15, [2011](/2011) as a companion to NAM 30, marked the inclusion of the long-awaited triple-tile 6-lane Avenue (AVE-6) and 7-lane Turning Lane Avenue (TLA-7), as well as the single-tile network now known as the 4-lane Narrow Road (NRD-4). Draggable width transitions were also integrated at this time.

The separate download NWM file was discontinued on March 2nd, [2013](/2013), when the mod was fully merged into NAM 31.0. The project has only seen minor improvements since that time, with a proposed IID scheme revamp similar to the RHW's "Project 57" being scrapped.

## Basic Network Characteristics

The NWM networks are all Override Networks, using Starter Piece Technology and extending on the Road and One-Way Road networks, both [Surface-type Networks](/transit-network#surface-networks). They do allow for direct access to RCI Zones. In order to function properly, the NWM, upon its release, will require the use of the NAM Unified Traffic Simulator. There are 13 networks in the current release, including 6 single-tile networks, 5 dual-tile networks, and 2 triple-tile networks. These comprise 5 basic network types, as outlined below.

### Turning Lane Avenues (TLAs)

Turning Lane Avenues (TLAs) are Road-based, despite the name. They incorporate a median left-turn lane to allow for left-turning motions across the roadway without interrupting through traffic flow. In the case of multi-tile TLAs, this allows for traffic to access zones on either side of the network.

**Single Tile:** TLA-3  
**Dual Tile:** TLA-5  
**Triple Tile:** TLA-7

A TLA-9 was also proposed at one time, with a prototype being developed, but with the controller size crisis issues that cropped up after NAM 31.0, it has been shelved indefinitely, due to the fact that this problem was related to crosslinking different [Override Networks](/override-networks).

### Avenues (AVEs)

NWM Avenues (AVEs) are Road-based, much like the TLAs. Like the default Avenue network that comes with the game, NWM Avenues feature a raised and landscaped median.

**Single Tile**: AVE-2  
**Triple Tile**: AVE-6

Just as was the case with the TLA-9, an AVE-8 was also planned. It has also been set aside for the same reasons. There has also been some talk of creating a "true AVE-4" using the same method as was used for the TLA-5, which, due to the fact that the TLA-5 uses a split-tile diagonal layout, rather than a shared-tile like the default Avenue network, would allow it to avoid the diagonal congestion issues that plague the latter.

### Roads (RDs)

The Wider Roads are, logicially, Road-based, and are medianless. Some of these networks were previously referred to as **Medianless Avenues** or **MAVEs**, but this name was dropped in favor of the Road designation, due to frequent user confusion between the dual-tile MAVE-6 and triple-tile AVE-6. RD networks with an asymmetrical lane configuration are prefaced with an "A" (i.e. ARD-3), while narrower versions are prefaced with "N" (i.e. NRD-4)

**Single Tile**: ARD-3 (2+1 setup), NRD-4 **Dual Tile**: RD-4, RD-6

A dual-tile ARD-4 (in a 3+1 lane configuration) has been rumored for eventual inclusion. The RD-type networks were never planned to be given triple-tile versions. Along the same lines of the "true AVE-4", there have been occasional whispers of a conversion mod, to make the default Avenue look like the RD-4, which also uses shared-tile diagonals.

### One-Way Roads (OWRs)

The NWM also includes additional width varieties of the game's default One-Way Road network, ranging from 1 to 5 lanes. There have been discussions of eventually converting the OWR-1 to a Street-based network to give it its own, separate capacity.

**Single Tile**: OWR-1, OWR-3  
**Dual Tile**: OWR-4, OWR-5

A dual-tile OWR-6 has also been rumored, with some textures being designed, but with the controller size matter and the role of crosslinking in that issue, it is unlikely to be explored further. There have also been plans to convert the OWR-1 to a Street-based setup, allowing it to have a lower capacity and satisfy long-running requests specifically for One-Way Streets, but the directionality issue and the more difficult method required to build diagonal Streets has put these plans on hold.

### Neighbor Connection

The single-tile Road-based networks can form normal neighbor connections. However, the Road-based multi-tile networks require Neighbor Connector Pieces. Neighbor connections with One-Way Roads are not possible.

### Future Plans

While additional network widths are not presently under consideration, there has been discussion of including elevated NWM networks, likely at L1 and L2, to fulfill that functional gap. In lieu of the AVE-8 and TLA-9, there has also been discussion of adding [Turn Lane Extension Pieces](/turn-lane-extension-pieces) to the OWR-4, to allow two parallel OWR-4s traveling in opposite directions to operate as a *de facto* AVE-8, complete with a higher network capacity.

## NWM Development Team & Contributors

### Current

- [Dexter](/people/dexter)
- [eggman121](/people/eggman121)
- [GDO29Anagram](/people/gdo29anagram)
- [jdenm8](/people/jdenm8)
- [memo](/people/memo)
- [michi_cc](/people/michi-cc)
- [Shadow Assassin](/people/shadow-assassin)
- [Tarkus](/people/tarkus)

### Former

- [beskhu3epnm](/people/beskhu3epnm)
- [jondor](/people/jondor)
- [Ryan B.](/people/ryan-b)
- [jplumbley](/people/jplumbley)
- [mikeseith](/people/mikeseith)
- [superhands](/people/superhands)

## See Also

- [Development thread](http://sc4devotion.com/forums/index.php?topic=1200.0)

> **Note:** This article needs expanding.
