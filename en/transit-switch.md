---
title: "Transit Switch"
description: ""
published: true
date: '2019-08-09T09:44:26Z'
tags: ["Modding Lots", "The Simulation"]
editor: markdown
dateCreated: '2008-08-30T19:35:41Z'
---

Transit switches occur when a [Sim](/sim), during the course of their commute, is required to move from one method of transportation to another, such as from walking (pedestrian) to getting on a bus. These switches are incorporated into lots (such as the bus station). Switches can impose a "cost" on transit to represent time that would be taken to use the facility, such as while waiting for the bus.

### Issue with Transit Switching

Early works with [Transit Enabling](/transit-enable) led to lots such as bus station on top of the road, or like the Game's version of the large rail station. In these situations, though the [automata](/automata) appear to move uninhibited through the lot, the Game's [Trip Calculator](/trip-calculator) sees this as the network ending, a station with the Sim disembarking, moving through the lot, and selecting their next means of transportation they will use. In the case of the road top bus station, the Sim will appear to continue through along his route, as would be expected. However, at a switch point like this, the trip calculator will recalculate all possible routes from that point using the remaining time for the commute. Not too much of a problem for a single Sim, but for a city of tens or hundreds of thousands, recalculating each trip every time can quickly become taxing on the simulator.

A more detailed discussion of Transit Switching, and also Network Enabling may be found at SC4Devotion (link pending)

> **Note:** This article needs expanding.
