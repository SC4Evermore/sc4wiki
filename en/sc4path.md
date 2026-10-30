---
title: "SC4Path"
description: ""
published: false
date: '2019-08-09T02:55:02Z'
tags: ["File Formats/SC4"]
editor: markdown
dateCreated: '2008-08-30T19:33:12Z'
---

**SC4Path** files define where the game's [automata](/automata) (Sims, vehicles and trains) travel on transit networks. SC4Path files have an [Instance ID](/instance-id) (IID) that matches that of the [exemplar](/exemplar) for the network piece involved. The [exemplar](/exemplar) for an orthogonal section of road, for instance, which ends in IID *0x00004b00* has a matching SC4Path file ending in that same IID. For puzzle pieces, the SC4Path has the same IID as the corresponding exemplar and [S3D](/s3d) files for the piece.

## SC4Path Format

> Main article: [SC4Path Format](/sc4path-format)

SC4Path files come in three different versions, namely 1.0, 1.1, and 1.2. The first two were included in the original release of [SimCity 4](/simcity-4), and the third was introduced in [Rush Hour](/rush-hour). All three versions can be used simultaneously in the game. The format of each version may vary slightly. Generally, SC4Path files begin with a header, containing version and file information, followed by repeating chunks of data that contain the actual path information.

Typically, when creating new paths and/or path files, try to use version 1.2 as it contains all formats of previous versions. Be mindful of changing the version of an existing file though, as all Paths within the file may need changing if the version is changed.

The [Group ID](/group-id) (GID) for path files is dependent on whether or not the network tile in-game is a 3D model or just a texture.

- SC4Path file GID for 3D Model tile(s): *0xA966883F*
- SC4Path file GID for Texture tile(s): *0x69668828*

## Types of Paths

There are two types of paths: **Normal Paths** and **Stop Paths**. Normal paths define where automata enter a tile, leave the tile, and the path it takes in between those points. Stop paths tell automata where to stop when a vehicle is crossing the path ahead, this is used at intersections to prevent collisions. Stop paths must always come after all normal paths in a SC4Path file.

## Troubleshooting with the DrawPaths Cheat

The <!-- unconverted template: plugin --> contains a very useful [cheat](/cheat) called *DrawPaths*. This cheat draws arrows showing the direction and location of paths on all network tiles. Typing a number after the cheat can limit the paths drawn. Paths will flash Red-White when their Entry/Exit points don't match the coordinates of the path, making testing the paths much easier than before when testers had to [UDI](/udi) through the tile on all possible paths. Stop Paths also appear as red crosses.

## Lag issues

If a path file is not included for a transit network it will cause the game to lag when dragging the network, this can be avoided by using a path file which contains no paths, but still has a header.

## Path Jumping

When [SimCity 4](/simcity-4) was originally released, cars could jump from a highway to a road below without the existence of any ramps under certain circumstances. This is something that Maxis fixed. Unfortunately, networks still have some limitations and/or issues with them related to paths, which subsequently affects normal path routing and also [U-Drive-It](/u-drive-it). These limitations/issues are more noticeable with some of the custom-made items that have been made for the game.

## Daeley's SC4Path Creator

<img src="/_files/images/pathcreator.jpg" title="A screenshot of the single tile frame." width="200" alt="A screenshot of the single tile frame." /> [BSC](/bsc) member [Daeley](/people/daeley) has created a tool to create and edit SC4Path files called [SC4 Path Creator](/sc4-path-creator). The tool is currently in version 1.60.

1.  [Network Specs/Paths](/network-specs/paths)
