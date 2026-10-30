---
title: "Introduction to the NWM"
description: ""
published: false
date: '2019-08-04T22:57:12Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2016-07-07T02:27:22Z'
---

The **Network Widening Mod** (abbreviated NWM) is a plugin within the NAM, which extends the default Roads and One-Way Road options using starter pieces and overrides, allowing width variants ranging from a single-lane One-Way Road, up to 7-lane Roads with center turn lanes. Started in 2006, and first released as part of the NAM 28 cycle in 2010, the NWM is a particularly sizable NAM plugin, incorporating a total of thirteen override networks. For a list of the networks contained in the NWM, see the [NWM Networks](/namdoc/nwm-networks) article.

## NWM Components and Features

- **[Starter Pieces](/namdoc/nwm-networks)**: The NWM Starter Pieces are the main driving force of the mod. They allow the game's default Road and One-Way Road networks to be transformed into the various configurations available in the NWM. When the Road or One-Way Road tool is dragged through a Starter Piece, the whole stretch will transform to match the corresponding Starter Piece. For two-way networks, the Road network is used, while for one-way networks, the One-Way Road network is used. Intersections are created just as one would build them with the default networks, by dragging the NWM override network up to or through the crossing network. There are limitations at present on intersections involving diagonals, however.

<!-- -->

- **[Transitions](/namdoc/nwm-transitions)**: These allow NWM networks to transition to the default Maxis networks, to other NWM networks, or RealHighways. Most NWM transitions can be built by draggable means. Puzzle piece versions still exist for many setups, though most puzzle-based setups are now obsolete.

<!-- -->

- **[Wide-Radius Curves](/namdoc/nwm-curves)**: These allow wider-radius curves with NWM networks. Currently, these exist in puzzle piece form only, and are limited to the single-tile NWM networks. The dual and triple-tile NWM networks do not currently support Wide-Radius Curves.

<!-- -->

- **[Neighbor Connectors](/namdoc/nwm-neighbor-connections)**: These allow the two-way multi-tile NWM networks to properly cross into neighboring city tiles. Note that there is no neighbor connection functionality for the One-Way Road-based networks.

<!-- -->

- **[Bridges (over water)](/namdoc/nwm-bridges)**: The NWM has limited support for bridges over bodies of water. Note that due to in-game restrictions on adjacent bridges, that the bridges of the dual-tile NWM networks must be constructed with the Avenue tool, instead of the Road or One-Way Road tool. Triple-tile bridges are *not possible* by standard means by virtue of this restriction.

<!-- -->

- **Turn Lane Support**: Currently, there is some support for NWM networks to create turn lanes using the **[Turn Lane Extension Pieces](/namdoc/turn-lane-extension-pieces) (TuLEPs)**. The NWM-related TuLEPs are due to be superseded by **[FLEX Turn Lanes](/namdoc/flex-turn-lanes) (FTL)** in a future release.

The NWM does **not** currently support elevated viaduct/overpass functionality of any kind. Other networks that have elevated functionality in draggable form can cross over NWM networks. Fractional Angle Networking is not available for NWM networks at present.

With respect to highway interchanges, the NWM has better support from the [RealHighway](/namdoc/introduction-to-the-rhw) (RHW) system than by the default Maxis Highways, as any interchange involving a highway and an NWM network must currently be constructed using modular means.

Additionally, there is no support at present for connecting NWM networks with the existing draggable [Roundabout](/namdoc/roundabouts) functionality, though several puzzle pieces exist to connect the ARD-3, RD-4, and RD-6 networks with roundabouts.

## Further Reading and Links

For a history of the NWM mod and its development, see the main [Network Widening Mod](/network-widening-mod) article.
