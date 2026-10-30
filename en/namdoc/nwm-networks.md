---
title: "NWM Networks"
description: ""
published: true
date: '2019-08-04T22:57:13Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2016-07-07T03:03:14Z'
---

The NWM mod currently includes a total of 13 different networks, including nine Road-based networks, and four new widths of One-Way Road. All NWM networks currently only exist in ground-level form, and elevated NWM viaducts are not presently possible.

## Basic Overview

The NWM relies on the game's base Road and One-Way Road network tools, coupled with starter pieces. The starter pieces transform these base networks into other configurations. Each of these possibilities is detailed below. NWM networks are based on the specific configuration, and the number of lanes they carry, i.e. TLA-5 or OWR-4, including the center turn lane (if present). The specific meanings of these types are detailed below.

### Using Starter Pieces

In order to transform the base Road or One-Way Road network into one of the NWM networks, first select the starter piece for the network you would like to build from the NWM Starter Pieces button, under the Roads menu. The first option that will appear upon clicking the button will be the 3-lane Turning Lane Avenue (TLA-3). To access the other possibilities, press TAB to cycle forward, or Shift-TAB to cycle in reverse through the options. (*Note: If you are playing the Steam version of the game, it is highly recommended that you change the Overlay Shortcut Keys, as their default setting of Shift-TAB makes navigating NAM menus considerably more difficult. This can be done by going to View \> Settings \> In-Game and selecting the "Overlay Shortcut Keys" box in the Steam Client.*)

Upon selecting the network you would like to build, plop the starter piece. The brown "construction lot" handle at one end will disappear after placing the starter, leaving a one-tile-long stretch of the network. To continue the network, select the Road or One-Way Road Tool, as indicated by the starter piece's in-game description, and drag the road tool through the starter piece. The Road or One-Way Road will convert to the network (or portion thereof) once you release the tool. For multi-tile networks, you'll need to drag the same network tool through all tiles to get the full network. If, after dragging, a portion of highway reverts to the base Road or One-Way Road network, or the tool turns red and prevents dragging, this means that the particular setup you have attempted to build is not supported.

*Side Note: The reason the Avenue tool is not used in creating NWM networks is because its status as a dual-tile network makes it less flexible, and complicates consistency with the triple-tile networks. Additionally, some of the dual-tile NWM networks require a wider footprint than the Avenue's "shared tile" diagonal setup allows.*

## Types of NWM Networks

NWM networks may consists of as few as one lane, and as many as seven for a two-way stretch. They are divided into several categories:

### Turning Lane Avenues (TLAs)

The **Turning Lane Avenues** (abbreviated **TLA**), despite their name, are Road-based networks, but take on an appearance that somewhat resembles the game's default Avenue network, but with a continuous center turn lane down the middle, instead of a landscaped divider. There are three TLA networks:

- **TLA-3**: 3-lane Turning Lane Avenue, a single-tile network with two travel lanes and one continuous center turn lane.
- **TLA-5**: 5-lane Turning Lane Avenue, a dual-tile network with four travel lanes and one continuous center turn lane.
- **TLA-7**: 7-lane Turning Lane Avenue, a triple-tile network with six travel lanes and one continuous center turn lane.

### "Avenues" (AVEs)

The NWM's **"Avenues"** (abbreviated **AVE**), are again, despite their name, are Road-based networks, but take on an appearance that resemble the game's default Avenue network, including the landscaped median. There are two AVE networks:

- **AVE-2**: 2-lane Avenue, a single-tile network with two travel lanes.
- **AVE-6**: 6-lane Avenue, a triple-tile network with six travel lanes.

### Roads (RDs)

The NWM's **Roads** (abbreviated **RD**), are Road-based networks, lacking a central median, like the game's default Road network. There are four RD networks:

- **ARD-3**: 3-lane Asymmetrical Road, a single-tile network with three travel lanes, with two in one direction, and one in the other.
- **NRD-4**: Narrow 4-lane Road, a single-tile network with four travel lanes.
- **RD-4**: 4-lane Road, a dual-tile network with four travel lanes.
- **RD-6**: 6-lane Road, a dual-tile network with six travel lanes.

<!-- -->

- *Note: It is possible to create a **ARD-5**, which contains three travel lanes in one direction, and two in the other, existing as a bybrid of the RD-4 and RD-6 networks. This configuration is supported to the same extent that the RD-4 and RD-6 are.*

### One-Way Roads (OWRs)

The NWM's **One-Way Roads** (abbreviated **OWR**), are One Way Road-based networks. There are four OWR networks added in the NWM:

- **OWR-1**: 1-lane One-Way Road, a single-tile network with one travel lane.
- **OWR-3**: 3-lane One-Way Road, a single-tile network with three travel lanes.
- **OWR-4**: 4-lane One-Way Road, a dual-tile network with four travel lanes.
- **OWR-5**: 5-lane One-Way Road, a dual-tile network with five travel lanes.

### Height Levels

NWM networks can only exist at ground-level. There is no elevated viaduct support.

### Capacities and Speeds

All NWM networks follow the catalog speeds of their respective base networks under the [NAM Traffic Simulator](/namdoc/overview-of-the-nam-traffic-simulator), either Road or One-Way Road. For Road-based NWM networks, the catalog speeds are 50km/h for Cars, 45km/h for Buses, and 40km/h for Freight Trucks. For One-Way Road-based NWM networks, the speeds are 75km/h for Cars, 65km/h for Buses, and 60km/h for Freight Trucks. Congestion can lower these speeds, and due to the workings of the simulator's *Congestion vs. Speed Curve*, the actual speed reached on the network can exceed these values in exceptionally light traffic.

The capacity of each NWM network depends on the version of the [NAM Traffic Simulator](/namdoc/overview-of-the-nam-traffic-simulator) one has installed, or the settings used in the [Traffic Simulator Configuration Tool (TSCT)](/namdoc/traffic-simulator-configuration-tool). SimCity 4 calculates capacity on a *per-tile* rather than a *per-lane* basis, so the width of the network on the game's grid is the main determining factor. NAM development has yielded a method for boosting per-tile capacity, known as *Distilled Intersection Paths (DIPs)*. Any network with DIPs receives a 25% bonus over the per-tile catalog capacity. The TLA-3, AVE-2, ARD-3, OWR-3, NRD-4, and RD-6 all have DIPs. Additionally, networks with crossing paths, including the TLA-5, OWR-4, OWR-5, TLA-7, and AVE-6, also invoke the same 25% per tile bonus. The only NWM networks without DIPs are the OWR-1 and RD-4.

|                     |             |         |            |          |           |
|---------------------|-------------|---------|------------|----------|-----------|
| **Network**         | **Classic** | **Low** | **Medium** | **High** | **Ultra** |
| **TLA-3** (1 tile)  | 1500        | 3000    | 5000       | 7500     | 15000     |
| **AVE-2** (1 tile)  | 1500        | 3000    | 5000       | 7500     | 15000     |
| **ARD-3** (1 tile)  | 1500        | 3000    | 5000       | 7500     | 15000     |
| **OWR-1** (1 tile)  | 1800        | 3600    | 6000       | 9000     | 18000     |
| **OWR-3** (1 tile)  | 2250        | 4500    | 7500       | 11250    | 22500     |
| **NRD-4** (1 tile)  | 1500        | 3000    | 5000       | 7500     | 15000     |
| **TLA-5** (2 tiles) | 3000        | 6000    | 10000      | 15000    | 30000     |
| **OWR-4** (2 tiles) | 4500        | 9000    | 15000      | 22500    | 45000     |
| **OWR-5** (2 tiles) | 4500        | 9000    | 15000      | 22500    | 45000     |
| **RD-4** (2 tiles)  | 2400        | 4800    | 8000       | 12000    | 24000     |
| **RD-6** (2 tiles)  | 3000        | 6000    | 10000      | 15000    | 30000     |
| **TLA-7** (3 tiles) | 13500       | 30000   | 50000      | 75000    | 150000    |
| **AVE-6** (3 tiles) | 13500       | 30000   | 50000      | 75000    | 150000    |

**Network Capacities for Full Network Width**

### Feature Support for Each Network

#### Intersection Support

Presently, all NWM networks support Orthogonal x Orthogonal (OxO) intersections and undercrossings with most other networks, both Maxis and NAM. To build these intersections, simply drag the NWM network through (or in the case of Ending T intersections, to) the crossing network. The overrides will convert the base network intersection to match that of the NWM network. A table showing the current OxO intersection support is below (under construction):

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Network** | **Street +** | **Street Thru T** | **Street Ending T** | **Road +** | **Road Thru T** | **Road Ending T** | **One-Way Road +** | **One-Way Road Thru T** | **One-Way Road Ending T** | **Avenue +** | **Avenue Thru T** | **Avenue Ending T (Short)** | **Avenue Ending T (Long)** | **Elevated Maxis Hwy** | **Rail (Dual-Track)** | **Rail (Single-Track)** | **GLR** | **Light Rail** | **Monorail** | **HSRP** |
| **TLA-3** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **AVE-2** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **ARD-3** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **OWR-1** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | No\* | Yes | Yes | No | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **OWR-3** | Yes | Yes | No | Yes | Yes | No\* | Yes | Yes | No\* | Yes | Yes | No | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **NRD-4** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |

**OxO Maxis and NAM Rail/Transit**

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Network** | **L0 RHW-2 +** | **L0 RHW-2 Thru T** | **L0 RHW-2 Ending T** | **L0 RHW-3 +** | **L0 RHW-3 Thru T** | **L0 RHW-3 Ending T** | **L0 RHW-4 +** | **L0 RHW-4 Thru T** | **L0 RHW-4 Ending T** | **L0 MIS +** | **L0 MIS Thru T** | **L0 MIS Ending T** | **Elevated RHW Networks** |

**OxO RHW**

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Network** | **TLA-3 +** | **TLA-3 Thru T** | **TLA-3 Ending T** | **AVE-2 +** | **AVE-2 Thru T** | **AVE-2 Ending T** | **ARD-3 +** | **ARD-3 Thru T** | **ARD-3 Ending T** | **OWR-1 +** | **OWR-1 Thru T** | **OWR-1 Ending T** | **OWR-3 +** | **OWR-3 Thru T** | **OWR-3 Ending T** | **NRD-4 +** | **NRD-4 Thru T** | **NRD-4 Ending T** |

**OxO NWM Single-Tile**

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Network** | **TLA-5 +** | **TLA-5 Thru T** | **TLA-5 Ending T (Short)** | **TLA-5 Ending T (Long)** | **OWR-4 +** | **OWR-4 Thru T** | **OWR-4 Ending T (Short)** | **OWR-4 Ending T (Long)** | **OWR-5 +** | **OWR-5 Thru T** | **OWR-5 Ending T (Short)** | **OWR-5 Ending T (Long)** | **RD-4 +** | **RD-4 Thru T** | **RD-4 Ending T (Short)** | **RD-4 Ending T (Long)** | **RD-6 +** | **RD-6 Thru T** | **RD-6 Ending T (Short)** | **RD-6 Ending T (Long)** | **TLA-7/AVE-6 +** | **TLA-7/AVE-6 Thru T** | **TLA-7/AVE-6 Ending T (Short)** | **TLA-7/AVE-6 Ending T (Long)** |

**OxO NWM Multi-Tile**

There is very limited support for NWM intersections and crossings in which crossing network and/or the NWM network are diagonal. This functionality is presently offered as-is, and only applies to select single-tile NWM networks. Dual and triple-tile networks presently lack any diagonal intersection capability, and will revert to their base network if attempted.

#### Transitions

*See [Namdoc:FLEX Turn Lanes](/namdoc/flex-turn-lanes) or [Namdoc:Turn Lane Extension Pieces](/namdoc/turn-lane-extension-pieces)*

#### Turn Lanes

*See [Namdoc:NWM Transitions](/namdoc/nwm-transitions)*

#### Wide-Radius Curves

Presently, Wide-Radius Curve functionality exists in puzzle piece form for the TLA-3, AVE-2, and ARD-3 networks. S-Curves, 45° Curves, and two radii of 90° Curves are available. There are no Wide-Radius Curves for the OWR-1, OWR-3, NRD-4, or any of the dual or triple-tile networks. Future curve functionality is expected to be added in draggable or FLEX form, following the Multi-Radius Curve concept.

#### Fractional Angle Networking

The NWM currently lacks any form of Fractional Angle Networking, though it is planned to receive this functionality at a later date. It will be implemented as a draggable setup.

## Further Aspects of Building NWM Systems

> **Note:** This article needs expanding.
