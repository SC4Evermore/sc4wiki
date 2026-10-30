---
title: "Introduction to the RHW"
description: ""
published: false
date: '2019-08-04T22:57:05Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2015-08-15T01:11:24Z'
---

The **RealHighway** Mod (abbreviated RHW) is a plugin within the NAM, which adds a new series of modular, variable-width Highway-type networks to the game, by re-purposing an unused network stub present in the game and extending it through the use of starter pieces and overrides. Started in 2005, it is presently the largest single plugin included in the NAM, adding over thirty override networks to the game, along with numerous ways of connecting these networks to one another, and to surface streets (i.e. Roads, Avenues).

## Differences Between RealHighways and Maxis Highways

There are some key differences in terms of how the RHW system operates, in comparison with the default Elevated and Ground "Maxis" Highways (MHW):

- Rather than one width and two height levels, RHW networks come in a variety of shapes and sizes, ranging from 2-lane rural highways to 10-lane freeways. All networks in the system can be built at three different height levels (Level 0/Ground, Level 1/7.5m, and Level 2/15.0m), with select networks being available at two additional height levels (Level 3/22.5m and Level 4/30.0m). There is also some support for Double-Decker Highways, with the two decks placed at Levels 1 and 2. A full listing of RHW networks can be found [here](/namdoc/rhw-networks).

<!-- -->

- The RHW is all about user customization and creativity, for those who want more precise control over constructing interchanges. While the Maxis Highway system includes all-in-one, prefabricated interchanges and overpasses that can be plopped or automatically constructed, RHW interchanges must be built manually, using a series of interchangeable, modular pieces. As such, the RHW is more complicated to use, and requires patience, but offers a much greater degree of control in the end. Recent versions have been geared toward making the RHW system more accessible, by migrating toward "FLEX" pieces that can be used by multiple networks, and with the start of the QuickChange system, which pre-assembles some common components into larger modules.

<!-- -->

- As evidenced by the "real" part of the name, the RHW is also about bringing at least some semblance of real-world scaling to SC4 highways. As such, transitions and interchanges may be larger, sometimes considerably, when compared to the compressed scale of the Maxis Highways.

## RHW Components

RHW items can be grouped into several basic categories. These include:

- - **[Base Network Tool](/namdoc/rhw-networks)**: By default, this produces the 2-lane, 2-way network, known as the **RHW-2** (as it contains 2 lanes across its full span).

<!-- -->

- - **[Starter Pieces](/namdoc/rhw-networks)**: Starter Pieces allow the base RHW-2 network to be transformed into all the other networks included in the mod. When the Base Network Tool is dragged through a Starter Piece, the whole stretch will transform to match the corresponding Starter Piece.

<!-- -->

- - **[Ramp Interfaces](/namdoc/rhw-ramp-interfaces)**: These are on/offramps, which allow an exit or entrance to split off the highway mainline. The ramp that branches off can subsequently be extended, by dragging with the Base Network Tool until meeting a surface street, another ramp interface (to connect two RHWs), or some variety of transition. Also included in this category are pieces to allow Volleyball Interchanges.

<!-- -->

- - **[Height Transitions](/namdoc/rhw-transitions)**: These allow one RHW network to transition to another height level--for instance, from Ground/Level 0 up to Level 1. These are necessary to build most interchanges, and come in two styles: On-Slope (built on the edge of an incline) and Ramp Style (which are built on flat ground). *Note: It is **highly recommended** to use the FLEXHeight transitions, which support all RHW networks and heights. The old transitions (including the curved MIS L0-L2 transition) are still available, but must be explicitly selected in the NAM installer.*

<!-- -->

- - **[Width Transitions](/namdoc/rhw-transitions)**: These allow one to add or subtract lanes from a given RHW network.

<!-- -->

- - **[FLEXFly](/namdoc/rhw-flexfly)**: These pieces allow for the construction of flyover ramps, of one or two-lane width, and at 45 or 90-degree angles, at various height levels.

<!-- -->

- - **[Wide Radius Curves](/namdoc/rhw-curves)**: These pieces allow for smoother curves on RHW networks.

<!-- -->

- - **[Fractional Angle Pieces](/namdoc/rhw-fractional-angles)**: These pieces allow for RHW networks to be built at angles other than the standard orthogonal and diagonal. Fractional Angle Ramp Interfaces are also available, which allow ramp branches at these fractional angles.

<!-- -->

- - **[Neighbor Connectors](/namdoc/rhw-neighbor-connections)**: These special pieces are required to build functional connections between two city tiles with multi-tile RHW networks.

<!-- -->

- - **[Cosmetic Pieces](/namdoc/rhw-cosmetic)**: These pieces allow one to customize the look of their RHW network, by adding different lane markings and arrows.

<!-- -->

- - **[Bridges (over water)](/namdoc/rhw-bridges)**: The RHW supports bridges over bodies of water for most networks. *Note that due to in-game restrictions on adjacent bridges, that the bridges of some wider RHW networks must be constructed with one of the Maxis Highway tools instead.*

<!-- -->

- - **[FLUPs (<em>FL</em>exible <em>U</em>nder<em>P</em>asses) Support Pieces](/namdoc/introduction-to-flups)**: These pieces allow the construction of Flexible Underpasses below various RHW networks. As of NAM 34, they are currently located under the *Road/RHW Interfaces* button (on the Roads menu).

<!-- -->

- - **[Other Special Pieces](/namdoc/rhw-special)**: These include the pieces to construct Diverging Diamond Interchanges (DDIs) and Single-Point Urban Interchanges (SPUIs). Both of these are currently located under the *Avenue/RHW Interfaces* button (on the Roads menu), which will become deprecated in a future release. *Please note that the FlexSPUI functionality is in a transitional state, and will have limited functionality until its upgrade is complete with NAM Version 36.*

<!-- -->

- - **[QuickChanges](/namdoc/rhw-quickchanges)**: QuickChanges (QCs) combine multiple smaller components into a larger modular piece, designed to speed up the construction of common interchange types. Typically, QuickChanges will combine a ramp interface with a height transition. Unlike the MHW interchanges, however, QuickChanges will omit the surface network, allowing a single QuickChange setup to be used for multiple surface network types.

<!-- -->

- - **[Road/RHW, One-Way Road/RHW, Avenue/RHW, and Rail/RHW Interfaces](/namdoc/viaduct-puzzle-pieces)**: These contain static puzzle pieces for building overpasses over ground-level RHW networks with surface streets or rail. Except for the Rail pieces, these are largely deprecated with the addition of the draggable versions of the Road, One-Way Road, and Avenue Viaducts. The Road, One-Way Road, and Avenue buttons are found under the Roads menu, while the Rail button is found under the Rails menu. *Note: The Diverging Diamond and (incomplete) FlexSPUI functionality is located under the Avenue/RHW Interfaces button, and RHW FLUPs features are under the Road/RHW Interfaces button.*

## Recommended Additions

Please note that in order to get the best RHW experience, there are other NAM components that come highly recommended:

- **[Draggable Road, One-Way Road, and Avenue Viaducts](/namdoc/draggable-viaducts)**: These allow for the base surface street networks to be elevated, in draggable form, which is extremely useful for building grade-separated interchanges with ground-level RHW networks.

<!-- -->

- **[Auto-Destructing Hole Diggers and Raisers](/namdoc/diggers-and-raisers)**: These are special versions of the old Hole Digger and Raiser lots which auto-destruct after placement. They are very useful for building embankments for both RHWs and surface streets crossing RHWs, and include all the height levels common for these networks.

It is also recommended that one use a **slope mod** (not included in the NAM) that supports the RHW network. Options include Ennedi's Slope Mod, or the dedicated RHW Slope Mod by bigdope404 (which can be used to supplement a slope mod that does not support the RHW.

## Further Reading and Links

For a history of the RHW mod and its development, see the main [RealHighway](/realhighway) article.
