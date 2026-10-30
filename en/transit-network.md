---
title: "Transit Network"
description: ""
published: true
date: '2020-02-15T06:20:36Z'
tags: ["Transit Networks", "Networks", "The Game"]
editor: markdown
dateCreated: '2008-06-03T02:42:51Z'
---

Transit Networks are draggable game items which allow vehicles, sims, and even utilities to get from one point to another. Some Transit Networks are also extended through ploppable segments, known as [Puzzle Pieces](/puzzle-piece), and in some cases, can be utilized to create [Override Networks](/override-network). The transport functionality of transit networks is enabled through [SC4Path Files](/sc4path), and their basic drawing routine is defined by the [RUL Files](/rul-file). In total, there are 13 different networks in SimCity 4.

## Road-Type Networks

The Road-Type Networks can be categorized in two types: Surface Networks and Highway Networks, based not only on their functionality, but also on their placement on the game menus.

### Surface Networks

Surface Networks are networks which are designed to allow direct access to and from [RCI Zones](/rci-zones) through all auto-based transit types (car, bus and freight truck), plus pedestrians (Sims). They are all found under the game's Roads menu. All RCI Zones must face a Surface Network in order to grow. There are four different Surface Networks in the game:

#### Streets

Streets are the lowest capacity network in-game, and can be built automatically as part of zone placement to ensure access. They are a 2-lane, 2-way network, covering 1 tile. It is a 2-dimensional, texture based network.

#### Roads

Roads are a 2-lane, 2-way network with a higher capacity than Streets, also covering 1 tile. It is a 2-dimensional, texture based network. It is a 2-dimensional, texture based network.

#### One-Way Roads

One-Way Roads, as the name implies, only allow traffic in one direction. Like Roads and Streets, they are a 2-lane network covering 1-tile, but by virtue of both lanes going in the same direction, they have a higher capacity than their 2-lane brethren. It is a 2-dimensional, texture based network.

#### Avenue

Avenues are the largest, highest-capacity Surface Network, with 4 lanes of traffic over 2 tiles, divided by a central median strip. Vehicles cannot cross this median strip without an intersection connecting the two sides of the Avenue. It is a 2-dimensional, texture based network.

#### Surface Street Override Networks

See [Street Addon Mod](/street-addon-mod) and [Network Widening Mod](/network-widening-mod).

### Highway Networks

Highway networks are generally high-speed, limited access thoroughfares. Only auto-based transit types can use them (car, bus and freight truck), and they cannot provide direct access to RCI Zones, so they must be interfaced with Surface Networks in order to create an effective, working road system.

#### Elevated Highway

The Elevated Highway (also just known as "Highways" in the game) is a 6-lane, 2-tile network, which is elevated to 15.5 meters. By virtue of being elevated, it can cross over all ground-based transit networks. It is strictly limited-access, and cannot create at-grade intersections, and connects to Surface Streets by Interchange Puzzle Pieces. It is a 3-dimensional, model based network.

#### Ground Highway

The Ground Highway is just like the Elevated Highway, except that it is not elevated. Surface Networks can go over the Ground Highway by overpasses, though overpass capabilities are more limited than those afforded by the Elevated Highway. It is a 3-dimensional, model based network.

#### Real Highway

*Main article: [Real Highway Mod](/real-highway-mod)*  
The Real Highway (RHW) is a network unhidden in the game by the Real Highway mod, released by the [NAM Team](/nam-team). It is based upon an unfinished network, dirtroads, Maxis left out of the [Rush Hour](/rush-hour) expansion pack, which the NAM Team was able to re-integrate into the game. It has been extended through a number of Override Networks, all of which are included in the RHW mod. It was formerly called the ANT(Additional Network Tool) It is a 2-dimensional, texture based network.

## Rail-Type Networks

Rail-Type networks are networks which utilize vehicles which run on rails. They can be found under the Rail and Misc. Transit menus in-game. Rail-Type networks generally cannot allow direct access to RCI Zones (the only exception being the Rail network's interaction with Industrial zones). They also do not allow Sims to directly reach their destination, and instead, [Stations](/stations) must be placed to allow Sims to get on and off the networks.

### Rail

The Rail network, sometimes referred to as **Heavy Rail**, allows for two different types of transit: Passenger Trains and Freight Trains. Traffic for each type can get on through either Passenger or Freight Stations. Industrial zones have the ability to place freight on Freight Trains on directly adjacent Rail networks without a station. It is a 2-dimensional, texture based network.

### Elevated Rail

The Elevated Rail network is the equivalent of real-world Light Rail systems. Passengers get on and off the network through stations. Because the network is elevated at 15.5 meters, it can cross over ground-level networks. It is a 3-dimensional, model based network.

### Monorail

The Monorail network functions like Elevated Rail, but is a quicker, more expensive rapid transit network. It is also elevated at 15.5 meters, and can cross over ground-level networks like other elevated networks. It is a 3-dimensional, model based network.

### Subway

The Subway network is an underground network (one of two in-game), which functions as a sort of extension of the Elevated Rail network, though the connection between the two must be facilitated through a [Transit Switch](/transit-switch). It is seen through the Underground View. Sims can get on and off the Subway network by stations which are generally placed over top of the line. Some of its properties are intertwined with the Water Pipe network and Road network. It is a 3-dimensional, model based network.

### Rail Override Extensions

See [Network Addon Mod](/network-addon-mod), [Ground Light Rail](/ground-light-rail), [High Speed Rail](/high-speed-rail).

## Utility-Type Networks

Utility-Type Networks do not carry traffic, but rather, resources necessary for one's city. Many of their properties are hardcoded, so it is nearly impossible to extend them further.

### Powerlines

As the name implies, Powerlines allow for electricity to go from [Power plants](/power-plant) (or [neighbor connections](/neighbor-connections) through [Neighbor Deals](/neighbor-deals)) to RCI Zones, and as [RCI Zones](/rci-zones) require power, they serve a vital purpose. Zones directly adjacent to power plants do not require powerline placement. It is a 3-dimensional, model based network. Powerlines are somewhat different to other networks in that they don't use the standard RUL files and can't be referenced in them, this is why diagonal power poles on water are possible.

### Water Pipes

Water Pipes allow for the transport of the [Water](/water) resource from [water towers](/water-tower) and [water pumps](/water-pump) (or [neighbor connections](/neighbor-connections)) to RCI Zones, which increases [Desirability](/desirability) for higher-wealth and higher-density occupants. Like Subways, Water Pipes are placed in the [Underground View](/underground-view). Water Pipes also allow connection into [Water Treatment Plants](/water-treatment-plants) to curb [Water Pollution](/water-pollution). Water Pipes are a 3-dimensional, model based network.

## Related Articles

- [Bridges](/bridges)

<!-- -->

- [Tunnels](/tunnels)

<!-- -->

- [Ferries](/ferry)

<!-- -->

- [Neighbor Connections](/neighbor-connections)

<!-- -->

- [Network Addon Mod](/network-addon-mod)

<!-- -->

- [Puzzle Piece](/puzzle-piece)

<!-- -->

- [Override Network](/override-network)
