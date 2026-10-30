---
title: "RUL File"
description: ""
published: false
date: '2021-02-19T10:56:51Z'
tags: ["File Formats/SC4", "Transit Modding"]
editor: markdown
dateCreated: '2008-07-27T23:23:18Z'
---

**RUL Files** are internal game files which control the placement of [Transit Network](/transit-network) items in-game. There are numerous RUL Files used by the game, each of which has its own particular function. There are three different types of RUL Files: [Network-Specific RUL Files](/individual-network-ruls), Multi-Network RUL Files, and [Bridge RULs](/bridge-rul). In addition, the [Network INI](/network-ini) file effectively functions like a RUL File. Because the format varies for each type of RUL File, the formats are covered on the individual pages for each RUL File type.

The function of the RUL File is defined by its [Instance ID](/instance-id). It is not possible to add new RUL Files, though it is possible to define new Bridge RULs for networks that do not already have them.

## Network-Specific RUL Files

> Main article: [Individual Network RULs](/individual-network-ruls)

Each in-game network has two Network-Specific RUL Files, one Main RUL which defines the basic placement of the network, and one Supplemental RUL, which defines same-network overrides. There are 24 total Network Specific RULs.

## Multi-Network RUL Files

There are three Multi-Network RUL Files, known by their IIDs: [RUL 0x10000000](/rul0) (RUL0), [RUL 0x10000001](/rul1) (RUL1) and [RUL 0x10000002](/rul2) (RUL2). These all handle situations that can involve multiple networks. RUL 0x10000000 is a particularly special case, since it deals exclusively with [ploppable network pieces](/puzzle-piece), as opposed to draggable network items. It is the only RUL file to do so. These three RUL files are often grouped in with [INI](/ini) files, for the similarity of their general format, in addition to the [Network INI](/network-ini) serving a similar purpose to these three RULs.

| Type ID | Group ID | Instance ID | Name | Description |
|----|----|----|----|----|
| 0x0a5bcf4b | 0xaa5bcf57 | 0x10000000 | [Intersection Ordering](/rul0) | RUL 0x10000000 |
| 0x0a5bcf4b | 0xaa5bcf57 | 0x10000001 | [Intersection Solutions](/rul1) | RUL 0x10000001 |
| 0x0a5bcf4b | 0xaa5bcf57 | 0x10000002 | [Network Overrides](/rul2) | RUL 0x10000002 |

## Bridge RULs

> Main article: [Bridge RUL](/bridge-rul)

Bridge RULs contain layout information for complex bridges, and allow for more control over custom bridges. Note that they are not required for all bridges, and not all network types have a corresponding Bridge RUL file.

## Network INI

> Main article: [Network INI](/network-ini)

The Network INI file, while technically not a RUL file, combines many functions of the various RUL files. Prior to the release of [Rush Hour](/rush-hour), this file contained all of the information that would eventually be split into the various RUL files. The extensive expansion of the transit networks with Rush Hour made containing all the network-related data in a single file impractical, and so the data was modularized into separate RUL Files. However, some network related information was left in the Network INI, such as: bridge shadows, Left-Hand Drive path substitution, power lines, and various bug fixes.

1.  [Network Specs](/network-specs)
