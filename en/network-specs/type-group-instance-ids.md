---
title: "Network Specs/Type, Group, Instance IDs"
description: ""
published: false
date: '2019-08-04T05:45:27Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-09T11:27:09Z'
---

[SimCity 4](/simcity-4) Networks have associated with it, at its most basic level, four different types of files that can stem from a RUL/INI file. These are:

- [Path files](#path-files)
- [FSH Files](#fsh-files)
- [Exemplar files](#exemplar-files)
- [S3D files](#s3d-files)

There are some other files involved, but these are the main ones that will be covered below.

These four mentioned file types are used when it comes to drawing a section of network, an intersection, a tunnel, and even bridges. For functionality reasons, certain *[Group IDs](/group-id)/GID* (and *[Instance IDs](/instance-id)/IIDs* in some cases) for these files need to be in place in order for some items to work properly. The following sections cover this in detail.

## Path Files

[Path](/sc4path) files have the following file format:

- Path file GID for 3D Model tile(s): 0xA966883F
- Path file GID for Texture tile(s): 0x69668828

If the in-game tile is a model, that is the [RUL](/rul) rule is referencing an [Exemplar](/exemplar) file (subsequently referencing a [S3D](/s3d) model file), then the Path file for that tile should have a GroupID of *0xA966883F*. If it does not have this GroupID, then the Path file may not actually be valid, and the in-game tile may not actually work properly.

If the in-game tile is a texture, that is the RUL rule is referencing a [texture](/texture) file, then the Path file for that tile should have a GroupID of *0x69668828*. If it does not have this GroupID, then the Path file may not actually be valid, and the in-game tile may not actually work properly.

## FSH Files

[FSH](/fsh) files for networks are actually covered by a 3D format (if only partially).

FSH files need to have a GroupID of *0xBADB57F1* or *0x1ABE787D* in order to be displayed properly (the latter is the standard GID used). This is especially more so when the FSH file is being used for, and referenced from, an S3D model file. There also exists a size limitation on FSH files (256x256 pixels) in order for them to work properly with the game (players using [Software Mode](/software-mode) have issues with textures over 256x256).

## Exemplar Files

[Exemplar](/exemplar) files’ GroupIDs are more complex (or there’s more to them). Essentially, Exemplar files reference S3D model files. The issue here is that these Exemplar files for the networks, in order to work properly in the game, must have a specific GroupID. Each of all the individual Networks, and/or particular areas of the Networks, have their own specific GroupID for these Exemplar files. Some of these are listed as follows:

- Power Poles
- 0x088E1962

<!-- -->

- Dirtroad (ANT/RHW)
- 0x6BE08658

<!-- -->

- Streets
- 0xA92A02EA

<!-- -->

- Roads
- 0x2821ED93

<!-- -->

- Onewayroads
- 0xCBE084CB

<!-- -->

- Avenue
- 0xCB730FAC

<!-- -->

- GroudHighway (MHW)
- 0xEBE084D1

<!-- -->

- Elevated Highway (MHW)
- 0xA8434037

<!-- -->

- Rail
- 0xE8347989

<!-- -->

- LightRail
- 0x2B79DFFB

<!-- -->

- Monorail
- 0xEBE084C2

There are some others than those listed above, but for all intents and purposes, these are the main ones. Remember, these IDs shown here are for GroupID of the Exemplar file that a particular RUL rule might be referencing (where applicable). Remember, any RUL file can reference an Exemplar. These GroupIDs are also applicable to references made out from the [Network INI](/network-ini) file and also Tunnels and bridges (bridges are a little more complex though).

## S3D Files

[S3D](/s3d) files for networks are covered by a specific 3D format. All network-based S3D files must contain the GroupID of *0xBADB57F1* in order to appear properly in-game.

## End notes

The whole aspect, from RUL through to drawing a section of network in-game, goes through a whole process of checking flags from various different items to make sure everything is valid. If one item, if one portion of that process does not pass a flag, then it can completely void the functionality of an item, and not work in-game. The same can be said for other areas of SimCity, not just the networks. Out of all the network aspects, very little of it is actually hardcoded. Tunnels, neighbour connections, Street diagonal functionality (or lack of it), are the few items controlled in a more direct fashion by the exe, and hence can not be changed via any of the RUL or related files. They can influence functionality of these items, but ultimately, they don’t control it.
