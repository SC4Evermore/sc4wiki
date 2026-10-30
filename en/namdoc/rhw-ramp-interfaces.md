---
title: "RHW Ramp Interfaces"
description: ""
published: true
date: '2019-08-04T22:57:09Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2015-11-30T08:12:13Z'
---

For most interchange construction situations with the RealHighways (RHWs), construction is achieved through modular means. The on and offramps from an RHW to either a surface street (i.e. a Road, Avenue, One-Way Road, or Network Widening Mod network) or another RHW are built using **ramp interfaces**, which create a ramp branch splitting off from an RHW, which can then be connected to the desired point. In the case of RHW networks with 6 or more lanes, ramp interfaces are the only means of connecting to other networks without a transition.

There are multiple means of constructing ramp interfaces, as well as a multitude of ramp interface types.

## Basic Usage

There are three methods for constructing RHW Ramp Interfaces, as described below. The Draggable Ramp Interfaces and FLEXRamp Interfaces are the preferred method for almost all situations, though some more specialized setups only exist as Puzzle Piece Ramp Interfaces (PPRIs). Regardless of the construction method, all ramp interfaces have two components in their overall structure: the **mainline**, which is the main through-traffic RHW route, and the **branch**, which is a ramp that juts out from the mainline on a ramp interface. The branch is used to connect from the mainline to either a surface street, or, in the case of an interchange between two RHWs, another ramp interface.

In the case of a ramp interface such as the **RHW-4 Type A1**, the name indicates that the mainline is an RHW-4, and "Type A1" is an indication of the angle and width of the branch, as well as whether or not the branch contains any "exit only" or "acceleration" lanes that are subtracted or added to the mainline. When the digit is 1, it is an indication that the branch has a single-lane MIS network branch. For more on the different types, see the [Ramp Interface Types and Nomenclature](/namdoc/rhw-ramp-interfaces#ramp-interface-types-and-nomenclature) section below.

<figure>
<img src="/_files/images/rhw-rampinterface-anatomy.jpg" title="Anatomy of a Ramp Interface (shown on RHW-2 Type A1)" width="400" />
<figcaption>Anatomy of a Ramp Interface (shown on RHW-2 Type A1)</figcaption>
</figure>

### Connecting from an RHW to an Road

The most basic situation one will encounter is in building an interchange between an RHW and a Road. The same method is essentially applicable to other surface networks, including Avenues, One-Way Roads, and NWM networks.

Once the ramp interface has been built, select the RHW Network Tool, and drag outward from the branch side of the ramp interface. Assuming one is using an interface with a single-lane branch (as from a Type A1 or B1 ramp interface) the MIS network will come out from the branch. Continue dragging the MIS ramp up toward the Road, to form a T-intersection. It can form an intersection just like most other networks. If you wish to continue the MIS ramp back to an RHW, continue dragging through the intersection, turning the T-intersection into a +-intersection. Assuming you've built an entrance ramp on your mainline farther down, simply continue dragging the MIS ramp until you hook it into the branch end of the entrance ramp interface. The MIS ramps may also curve between the ramp interface and the surface street connection as needed.

Assuming this has all been done at ground level, it won't be of much use as far as a grade-separated interchange goes. In order to separate the grade and build a proper interchange, [Height Transitions](/namdoc/rhw-transitions) or the [Draggable Road Viaducts](/namdoc/draggable-viaducts) will become necessary. The options would be to: (a) raise the RHW mainline's height so it crosses over the Road, (b) elevated the Road using the Draggable Viaducts and also use a Height Transition to raise the MIS ramp branch to meet the viaduct, or (c) elevate the Road with the Draggable Viaducts, and curve the ramp branch to a point where it can meet the Road while it is at ground level. The [QuickChange](/namdoc/rhw-quickchange) system can accelerate Option B.

### Connecting an RHW to Another RHW

The process of connecting two different RHW mainlines is even simpler in theory. Simply drag out the ramp branch from the exit ramp interface on one of the RHWs, and connect it to the entrance ramp interface on the other RHW. This process can become considerably more complicated when the connection ramp must cross over one or both highways, in which case, [Height Transitions](/namdoc/rhw-transitions) and [FLEXFly](/namdoc/flexfly) pieces may be a required part of the solution. More details on this process can be found in the section on [Building Interchanges with the RHW](/namdoc/rhw-interchanges).

## Ramp Interface Types and Nomenclature

There are two, sometimes three or even four parts to the name of each ramp interface type. These indicate the mainline width, the branch angle and width, as well as whether any of the branch lanes were "exit only" or "acceleration" lanes, added or subtracted from the mainline. Some more specialized ramp interfaces may append that fourth part, containing other information about the nature and location of the branch in relation to the mainline.

The mainline portion will always indicate the width of the "top" portion of the ramp interface, where the mainline is guaranteed to be at its widest. In the case of FLEXRamps, since they are often shared by multiple networks, which override a base version, the mainline network is usually excluded from the in-game description. For the "type" designation, the number indicates the number of lanes included in the branch, while the letter indicates the branch angle and indicates whether the branch has any lanes that peel off (on exit) or join (on entrance) the mainline. The letter/number types translate as follows:

- **A1**: Indicates a single-lane (MIS) branch off the mainline, with an orthogonal branch. No lanes peel off the mainline.
- **B1**: Indicates a single-lane (MIS) branch off the mainline, with a diagonal branch. No lanes peel off the mainline.
- **C1**: Indicates a single-lane (MIS) branch off the mainline, with a fractional angle (18.4 degrees) branch. No lanes peel off the mainline.
- **D1**: Indicates a single-lane (MIS) branch off the mainline, with an orthogonal branch. The branch is formed from one lane of the mainline, and the mainline has one fewer lane at the bottom.
- **E1**: Indicates a single-lane (MIS) branch off the mainline, with a diagonal branch. The branch is formed from one lane of the mainline, and the mainline has one fewer lane at the bottom.
- **F1**: Indicates a single-lane (MIS) branch off the mainline, splitting at a fractional angle (18.4 degrees) from the mainline. The branch is formed from one lane of the mainline, and the mainline has one fewer lane at the bottom.
- **A2**: Indicates a dual-lane (RHW-4) branch off the mainline, with an orthogonal branch. One of the two lanes on the branch is from the mainline, and the mainline has one fewer lane at the bottom.
- **B2**: Indicates a dual-lane (RHW-4) branch off the mainline, with a diagonal branch. One of the two lanes on the branch is from the mainline, and the mainline has one fewer lane at the bottom.
- **C2**: Indicates a dual-lane (RHW-4) branch off the mainline, with a fractional angle (18.4 degrees) branch. One of the two lanes on the branch is from the mainline, and the mainline has one fewer lane at the bottom.
- **D2**: Indicates a dual-lane (RHW-4) branch off the mainline, with an orthogonal branch. Both lanes on the branch are from the mainline, and the mainline has two fewer lanes at the bottom.
- **E2**: Indicates a dual-lane (RHW-4) branch off the mainline, with a diagonal branch. Both lanes on the branch are from the mainline, and the mainline has two fewer lanes at the bottom.
- **F2**: Indicates a dual-lane (RHW-4) branch off the mainline, with a fractional angle (18.4 degrees) branch. Both lanes on the branch are from the mainline, and the mainline has two fewer lanes at the bottom.
- **A3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with an orthogonal branch. Two of the three lanes on the branch is from the mainline, and the mainline has two fewer lanes at the bottom. There are currently no Type A3 ramps available.
- **B3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with a diagonal branch. Two of the three lanes on the branch is from the mainline, and the mainline has two fewer lanes at the bottom. There are currently no Type B3 ramps available.
- **C3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with a fractional angle (18.4 degrees) branch. Two of the three lanes on the branch is from the mainline, and the mainline has two fewer lanes at the bottom.
- **D3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with an orthogonal branch. All three lanes on the branch are from the mainline, and the mainline has three fewer lanes at the bottom.

There are currently no Type D3 ramps available.

- **E3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with a diagonal branch. All three lanes on the branch are from the mainline, and the mainline has three fewer lanes at the bottom.

There are currently no Type E3 ramps available.

- **F3**: Indicates a triple-lane (RHW-6S) branch off the mainline, with a fractional angle (18.4 degrees) branch. All three lanes on the branch are from the mainline, and the mainline has three fewer lanes at the bottom. There are currently no Type F3 ramps available.

The additional modifiers with some of the more specialized ramp interfaces indicate the following:

- **Inside**: This designation is seen on ramps from one-way RHW networks, and indicates that the ramp branch is on the inside (left exit/entrance in countries with right-hand traffic, right exit/entrance for those with left-hand traffic), rather than the expected outside.
- **Wide**: This designation indicates that the ramp branch has a larger separation than the standard version of that type, and is most commonly applied to A1 and A2 ramps.
- **Wye**: This designation indicates that both the branch and the mainline (often when the mainline is of the same width as the branch) both diverge from the path of the mainline at the top in a symmetrical fashion, forming a wishbone or Y-shape.
- **Shift**: This is an indication that the mainline undergoes curvature in the midst of the ramp. This occurs when the mainline shifts from an S-type network to a C-type network.
- **Dual**: This is an indication that there are two ramp branches on the ramp interface. This is most commonly seen with the bidirectional networks (RHW-2, RHW-3, and Double-Decker RHWs), or in conjunction with Shift.
- **Folded**: This is an indication that there are two ramp branches that curve off at 90-degree angles, in opposite directions. There is only one Folded ramp interface, the RHW-2 D1 Folded.
- **Diagonal**: This designation indicates that the mainline is diagonal rather than orthogonal. The branch angles are handled the same as if the ramp were orthogonal (i.e. an orthogonal ramp branch off a diagonal ramp interface would still be an A or D-type ramp of some sort).
- **FA**: This designation indicates that the mainline is at a fractional angle rather than orthogonal. The branch angles are handled the same as if the ramp were orthogonal (i.e. an orthogonal ramp branch off an FA ramp interface would still be an A or D-type ramp of some sort).

## Constructing Ramp Interfaces

There are three different methods for constructing ramp interfaces: the Draggable Ramp Interfaces, FLEXRamps, and Puzzle Piece Ramp Interfaces. The first two are the preferred method for building exits and entrances to your RHWs, but there are still a few more specialized setups that can only be found in puzzle piece form.

### Draggable Ramp Interfaces (DRIs)

Draggable Ramp Interfaces, or DRIs, are ramp interfaces that are constructed through draggable means. With the exception of a very few specialized setups, virtually all RHW ramp interface setups can be built through draggable means. Each ramp interface type supported by the system has a special drag pattern, which, when constructed, will subsequently convert into the appropriate on/offramp. The below Table of DRI Patterns shows the exit ramp (entrance ramp for Left-Hand Traffic) setup. The corresponding entrance (or exit in Left-Hand Traffic) can be constructed by using the mirror image of these patterns.

Elevated ramp interfaces can be constructed by dragging the appropriate elevated RHW network (L1-L4) or double-decker RHW through the DRI, which, provided the particular setup is supported by that network, will elevate the ramp. Many setups for narrower networks can be transformed into corresponding versions for wider networks by using the same method. This conversion is most reliable if the overriding network is dragged into the top end of the mainline.

<figure>
<img src="/_files/images/dri-table.png" title="Table of DRI Patterns by [woodb3kmaster](/people/woodb3kmaster)" />
<figcaption>Table of DRI Patterns by [woodb3kmaster](/people/woodb3kmaster)</figcaption>
</figure>

Below is a chart of which networks support which ramp interface types (under construction):

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Network** | **Type A1** | **Type B1** | **Type C1** | **Type D1** | **Type E1** | **Type F1** | **Type A2** | **Type B2** | **Type C2** | **Type D2** | **Type E2** | **Type F2** | **Type C3** | **Type A1 Inside** | **Type B1 Inside** | **Type C1 Inside** | **Type D1 Inside** | **Type E1 Inside** | **Type F1 Inside** | **Type A1 Dual** | **Type B1 Dual** | **Type A1/B1 Dual** | **Type C1 Dual** |
| **L0 RHW-2** | Yes | Yes | Yes (PP only) | Yes | Yes | Yes (PP only) | No | No | No | No | No | No | No | No | No | No | No | No | No | Yes | Yes | Yes (DRI only) | Yes (PP only) |

**Supported Orthogonal Ramp Interface Types for Each network**

### FLEXRamp Interfaces

FLEXRamps, introduced in the NAM 31 release of March [2013](/2013), work similarly to the DRIs in function, but are constructed as FLEX pieces, and accessed through the FLEXRamp button under the Highways menu. The main advantages of the FLEXRamps over DRIs is that they there are no drag patterns to remember, and they are more slope tolerant.

There are a total of 12 FLEXRamps included in the mod, all of which use the narrowest ground-level mainline available for that ramp type configuration, which is listed for each piece. (Note that the D1 and E1 must use the RHW-4, however, due to override issues with MIS directionality that would be created if the RHW-2 were used instead.) Each FLEXRamp can be overridden to any other RHW network width or height that supports that configuration, by dragging a section of that network into the top side of the ramp interface. Any network supported by the DRI version of each ramp interface type will also be supported by the corresponding FLEXRamp.

There are also two FLEXRamp setups that are not possible with the DRIs at present, those being the two diagonal ramp interface setups.

1.  Type A1 (Base: RHW-2)
2.  Type B1 (Base: RHW-2)
3.  Type D1 (Base: RHW-4)
4.  Type E1 (Base: RHW-4)
5.  Diagonal Type A1 (Base: RHW-2)
6.  Diagonal Type B1 (Base: RHW-2)
7.  Type A2 (Base: RHW-6S)
8.  Type B2 (Base: RHW-6S)
9.  Type D2 (Base: RHW-6S)
10. Type E2 (Base: RHW-6S)
11. Type A1 Inside (Base: MIS Ramp)
12. Type B1 Inside (Base: MIS Ramp)

With the RHW-2 network, a Type A1 or Type B1 exit and entrance can be stacked on one another to form Type A1 Dual or B1 Dual, respectively.

Image:Rhw-flexramp-1-6-nam34.jpg\|1 through 6 Image:Rhw-flexramp-7-10-nam34.jpg\|7 through 10 Image:Rhw-flexramp-11-12-nam34.jpg\|11 and 12

### Puzzle Piece Ramp Interfaces (PPRIs) and Volleyball Interchange Pieces

Puzzle Piece Ramp Interfaces were the only method for constructing ramp interfaces between the introduction of the Modular Interchange System in RHW 2.0/NAM 22 (January [2008](/2008)) and the introduction of DRIs in RHW 4.0/NAM 28 (May [2010](/2010)). They are found under the Ramp Interfaces button on the Highways menu. However, with major upgrades to the DRI and FLEXRamp systems in NAM 33 in November [2015](/2015), the puzzle piece ramp interfaces are largely obsolete, with the exception of a few setups that have not yet received new implementations. The pieces for constructing Volleyball Interchanges are also located under this button.

With NAM 33, the item order under this button was changed, to put the pieces not yet replaced by FLEXRamp or DRI solutions at the front of the TAB Loop. The pieces after the Volleyball Interchange items all have DRI/FLEXRamp equivalents, which should be used instead. The deprecated PPRIs that have been rendered obsolete by other methods are no longer supported, and only remain for legacy purposes.

The ramp interfaces that handle Fractional Angle Networks (Type C and Type F) only come in puzzle piece form at present. They are, however, located under a different menu button, which deals specifically with Fractional Angle ramp interfaces. More information on these ramps can be found under the [Fractional Angle RHW](/namdoc/rhw-fractional-angles) article. The Avenue network also has three puzzle-based ramp interfaces with MIS branches as well, (Type A1, Type B1, and Type C1) which can be found at the end of the Avenue/RHW Interfaces button, on the Roads menu.

> **Note:** This article needs expanding.
