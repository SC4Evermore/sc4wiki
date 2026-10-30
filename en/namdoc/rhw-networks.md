---
title: "RHW Networks"
description: ""
published: false
date: '2019-08-04T22:57:08Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2015-11-30T07:59:33Z'
---

The RHW mod currently includes a total of 34 different networks, comprising nine different widths, all of which have at least three different height levels, and some as many as five, plus one double-deck network. Due to the modular nature of some of these networks, various hybrids are also possible.

## Basic Overview

The RHW includes its own network tool, the RHW Tool, which produces the base two-lane, two-way RHW. As a full stretch of this network allowing traffic in both directions consists of two lanes, this network is known as the **RHW-2**. The remaining 33 networks included in the mod are effectively "pseudo-networks", which are created by the use of starter pieces to transform the base RHW-2 into other configurations. Each of these possibilities is detailed below.

### Using Starter Pieces

In order to transform the RHW-2 into one of the other RHW networks, first select the starter piece for the network you would like to build from the RHW Starter Pieces button, under the Highways menu. The first option that will appear upon clicking the button will be the RHW-4. To access the other possibilities, press TAB to cycle forward, or Shift-TAB to cycle in reverse through the options.

Upon selecting the network you would like to build, plop the starter piece. The brown "construction lot" handle at one end will disappear after placing the starter, leaving a one-tile-long stretch of the network. To continue the network, select the RHW Tool, and drag the RHW Tool through the starter piece. The RHW-2 will convert to the network (or portion thereof) once you release the tool. If, after dragging, a portion of highway reverts to RHW-2, or the tool turns red and prevents dragging, this means that the particular setup you have attempted to build is not supported.

*Side Note: The reason the RHW Tool exists is because Maxis left an unfinished stub of a network in place after the Rush Hour Expansion, known internally as "DirtRoad". Early NAM developers re-activated this tool for in-game use, but various street texture mods already fulfilled users' needs for dirt roads, and the tool's behavior was found to be more highway-like in nature. Adding any true new network tools beyond this is not truly possible without substantially re-writing the game's executable. For a history of the RHW's development, see the regular [RealHighway](/realhighway) page.*

### Building Diagonals

For the RHW networks that are single-tile, or have individual carriageways that are single-tile (MIS, RHW-4, and RHW-6S), diagonals may be built just like with any other network. Special care is needed with the wider RHW networks (RHW-6C, 8C, 8S, and 10S), which require a "split tile" diagonal setup. To build a split tile setup, treat each tile making up the full width as if it is its own network, and ensure that the tiles do not touch each other (which would create a "shared tile" setup).

## Types of RHW Networks

RHW networks may consists of as few as two lanes, and as many as ten for a two-way stretch. In addition, there are multiple ways to achieve certain numbers of lanes, and multiple height levels at which the highways may be elevated.

The basic width configurations are as follows:

- RHW-2 (RealHighway, 2-lane) - 1-tile width bi-directionally
- RHW-3 (RealHighway, 3-lane) - 1-tile width bi-directionally
- MIS Ramp (Modular Interchange System Ramp, 1-lane) - 1-tile with uni-directionality, 2-tile width bi-directionality
- RHW-4 (RealHighway, 4-lane) - 1-tile width uni-directionality, 2-tile width bi-directionality
- RHW-6S (RealHighway, 6-lane Separable) - 1-tile width uni-directionality, 2-tile width bi-directionality (*Note: The RHW-6S has a slight overhang onto additional tiles on its outer shoulder.*)
- RHW-6C (RealHighway, 6-lane Combined) - 3-tile width bi-directionality
- RHW-8S (RealHighway, 8-lane Separable) - 2-tile width uni-directionality, 4-tile width bi-directionality
- RHW-6C (RealHighway, 8-lane Combined) - 3-tile width bi-directionality
- RHW-10S (RealHighway, 10-lane Separable) - 2-tile width uni-directionality, 4-tile width bi-directionality

<!-- -->

- *A starter also exists for an "RHW-7C", which is a hybrid of the RHW-6C and RHW-8C. Similarly, a theoretical "RHW-9S" could be created by having RHW-8S for one direction, and RHW-10S for the other.*

### S-Type vs. C-Type

With some of the wider RHW options, with 6 or more lanes, two configurations may exist, an S-Type and a C-Type, i.e. the RHW-6S and the RHW-6C. In this scenario, the S stands for "Separable", while the C stands for "Combined". The "Separable" networks, such as the RHW-6S, can have splits between the directions of traffic, or carriageways, allowing for variable width medians. Two RHW-6S segments, one in each direction, may be directly adjacent, or they could be separated by the entire width of a city tile, in theory. With the "Combined" networks, such as the RHW-6C, there is a central median tile with barriers, and the two directions or carriageways are not separable from one another, and must be directly adjacent. The number of lanes on either side of this central median tile may still vary, and a special starter exists for an "RHW-7C", in which one side carries four lanes, while the other has only three.

### Height Levels

Each RHW network can be elevated above ground level, to at least two levels. These levels are typically abbreviated **Lx**, where *x* is the code for the particular height level, i.e. L0 for ground level. The other elevated heights indicate increments of 7.5 meters, such that:

- L1 = 7.5 meters
- L2 = 15 meters
- L3 = 22.5 meters
- L4 = 30 meters.

L1 and L2 are available for all networks, while L3 and L4 are only available for the RHW-4, RHW-6S, and the MIS Ramp.

The RHW-4 is a special case, in that it also has a double-decker variant, known as the DDRHW-4. The upper deck is situated at L2, while the lower deck is at L1.

The height nomenclature used for the elevated RHW networks is also generally carried over throughout the rest of the NAM, including the [Elevated Road Viaducts](/namdoc/draggable-viaducts).

### RHW Starter Pieces Button Content Listing

There are a total of 36 starter pieces under the RHW Starter Pieces Button:

1.  L0 RHW-4 Starter Piece
2.  L0 MIS Starter Piece
3.  L0 RHW-3 Starter Piece
4.  L0 RHW-6S Starter Piece
5.  L0 RHW-6C Starter Piece
6.  L0 RHW-8S Starter Piece
7.  L0 RHW-8C Starter Piece
8.  L0 RHW-7C Starter Piece
9.  L0 RHW-10S Starter Piece
10. L1 RHW-2 Starter Piece
11. L1 RHW-4 Starter Piece
12. L1 MIS Starter Piece
13. L1 RHW-3 Starter Piece
14. L1 RHW-6S Starter Piece
15. L1 RHW-6C Starter Piece
16. L1 RHW-8S Starter Piece
17. L1 RHW-8C Starter Piece
18. L1 RHW-7C Starter Piece
19. L1 RHW-10S Starter Piece
20. L2 RHW-2 Starter Piece
21. L2 RHW-4 Starter Piece
22. L2 MIS Starter Piece
23. L2 RHW-3 Starter Piece
24. L2 RHW-6S Starter Piece
25. L2 RHW-6C Starter Piece
26. L2 RHW-8S Starter Piece
27. L2 RHW-8C Starter Piece
28. L2 RHW-7C Starter Piece
29. L2 RHW-10S Starter Piece
30. L3 RHW-4 Starter Piece
31. L3 MIS Starter Piece
32. L3 RHW-6S Starter Piece
33. L4 RHW-4 Starter Piece
34. L4 MIS Starter Piece
35. L4 RHW-6S Starter Piece
36. DD RHW-4 Starter Piece (L1/L2)

### Capacities and Speeds

All RHW networks are set to a catalog speed of 150km/h for Cars and Buses, and 130km/h for Freight Trucks. Congestion can lower these speeds, and due to the workings of the simulator's *Congestion vs. Speed Curve*, the actual speeds reached on the network can exceed these value in exceptionally light traffic.

The capacity of each RHW network depends on the version of the [NAM Traffic Simulator](/namdoc/overview-of-the-nam-traffic-simulator) one has installed, or the settings used in the [Traffic Simulator Configuration Tool (TSCT)](/namdoc/traffic-simulator-configuration-tool). SimCity 4 calculates capacity on a *per-tile* rather than a *per-lane* basis, so the width of the network on the game's grid is the main determining factor. NAM development has yielded a method for boosting per-tile capacity, known as *Distilled Intersection Paths (DIPs)*. Any network with DIPs receives a 25% bonus over the per-tile catalog capacity. The RHW-3, RHW-6S, and DDRHW-4 all have DIPs. Additionally, networks with crossing paths, such as all of the C-type networks, as well as the RHW-8S and 10S, also invoke the same 25% per tile bonus.

|                       |             |         |            |          |           |
|-----------------------|-------------|---------|------------|----------|-----------|
| **Network**           | **Classic** | **Low** | **Medium** | **High** | **Ultra** |
| **RHW-2** (1 tile)    | 2700        | 6000    | 10000      | 15000    | 30000     |
| **RHW-3** (1 tile)    | 3375        | 7500    | 12500      | 18750    | 37500     |
| **MIS Ramp** (1 tile) | 2700        | 6000    | 10000      | 15000    | 30000     |
| **RHW-4** (2 tiles)   | 5400        | 12000   | 20000      | 30000    | 60000     |
| **RHW-6S** (2 tiles)  | 6750        | 15500   | 25000      | 37500    | 75000     |
| **RHW-6C** (3 tiles)  | 10125       | 22500   | 37500      | 56250    | 112500    |
| **RHW-8S** (4 tiles)  | 13500       | 30000   | 50000      | 75000    | 150000    |
| **RHW-8C** (3 tiles)  | 10125       | 22500   | 37500      | 56250    | 112500    |
| **RHW-10S** (4 tiles) | 13500       | 30000   | 50000      | 75000    | 150000    |
| **DDRHW-4** (1 tile)  | 3375        | 7500    | 12500      | 18750    | 37500     |

**Network Capacities for Full Network Width**

### Basic Feature Support for Each Network

**LEGEND**

OxO = Orthogonal x Orthogonal Crossing

OxD = Orthogonal x Diagonal Crossing

DxO = Diagonal x Orthogonal Crossing

DxD = Diagonal x Diagonal Crossing

|  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|
| **Network** | **At-Grade Intersections**\* | **Ramp Interfaces** | **Draggable Transitions to Non-RHW Networks** | **OxO with RHWs at Other Heights** | **OxD/DxO with RHWs at Other Heights** | **DxD with RHWs at Other Heights** | **Bridges over Water** |
| **L0 RHW-2** | Yes | Yes | Yes (Road, Avenue, TLA-3, AVE-2, NRD-4) | Yes | Yes | Yes | Yes |
| **L0 RHW-3** | Yes (No Avenues or NWM Networks, Limited Diagonals) | Yes | Yes (ARD-3) | Yes | Yes | Yes | No |
| **L0 MIS** | Yes | Yes | Yes (One-Way Road) | Yes | Yes | Yes | Yes |
| **L0 RHW-4** | Yes (No Avenues or NWM Networks) | Yes | Yes (One-Way Road, Avenue, Ground Maxis Highway, TLA-5, RD-4) | Yes | Yes | Yes | Yes |
| **L0 RHW-6S** | No | Yes | Yes (OWR-3, RD-6) | Yes | Yes | Yes | Yes |
| **L0 RHW-6C** | No | Yes | Yes (TLA-7, AVE-6) | Yes | Yes | Yes | No |
| **L0 RHW-8S** | No | Yes | No | Yes | Yes | Yes | Yes (MHW-based) |
| **L0 RHW-8C** | No | Yes | No | Yes | Yes | Yes | No |
| **L0 RHW-10S** | No | Yes | No | Yes | Yes | Yes | Yes (MHW-based) |
| **L1 RHW-2** | Yes | Yes | No | Yes | Yes | Yes | No |
| **L1 RHW-3** | No | No | No | Yes | Yes | Yes | No |
| **L1 MIS** | Yes | Yes | No | Yes | Yes | Yes | No |
| **L1 RHW-4** | No | Yes | Yes (L1 AVE Viaducts) | Yes | Yes | Yes | No |
| **L1 RHW-6S** | No | Yes | No | Yes | Yes | Yes | No |
| **L1 RHW-6C** | No | Yes | No | Yes | Yes | No | No |
| **L1 RHW-8S** | No | Yes | No | Yes | Yes | No | No |
| **L1 RHW-8C** | No | Yes | No | Yes | Yes | No | No |
| **L1 RHW-10S** | No | Yes | No | Yes | Yes | No | No |
| **L2 RHW-2** | Yes | Yes | No | Yes | Yes | Yes | No |
| **L2 RHW-3** | No | No | No | Yes | Yes | Yes | No |
| **L2 MIS** | Yes | Yes | No | Yes | Yes | Yes | Yes |
| **L2 RHW-4** | No | Yes | Yes (L2 AVE Viaducts, Elevated MHW with MHO) | Yes | Yes | Yes | Yes |
| **L2 RHW-6S** | No | Yes | No | Yes | Yes | Yes | No |
| **L2 RHW-6C** | No | Yes | No | Yes | Yes | No | No |
| **L2 RHW-8S** | No | Yes | No | Yes | Yes | No | No |
| **L2 RHW-8C** | No | Yes | No | Yes | Yes | No | No |
| **L2 RHW-10S** | No | Yes | No | Yes | Yes | No | No |
| **L3 MIS** | No | Yes | No | Yes | Yes | Yes | No |
| **L3 RHW-4** | No | Yes | No | Yes | Yes | Yes | No |
| **L3 RHW-6S** | No | Yes | No | Yes | Yes | Yes | No |
| **L4 MIS** | No | Yes | No | Yes | Yes | Yes | No |
| **L4 RHW-4** | No | Yes | No | Yes | Yes | Yes | No |
| **L4 RHW-6S** | No | Yes | No | Yes | Yes | Yes | No |
| **DD RHW-4** | No | Yes | No | Yes | Yes | Yes | Yes |

**Network Feature Support**

- At-Grade Intersection support *excludes* diagonal NWM intersections. Additionally, the Draggable Elevated Road, One-Way Road, and Avenue Viaducts do not support any crossings involving diagonals at present.

## Further Aspects of Building RHW Systems

> **Note:** This article needs expanding.
