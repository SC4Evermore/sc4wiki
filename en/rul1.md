---
title: "RUL1"
description: ""
published: false
date: '2019-08-09T22:35:50Z'
tags: ["NAM", "RUL Files", "Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2019-08-09T22:35:50Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">RUL1</th></tr>
<tr><td><strong>Name</strong></td><td>Intersection Solutions RUL</td></tr>
<tr><td><strong>Format</strong></td><td><a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x0A5BCF4B</td></tr>
<tr><td><strong>Group</strong></td><td>0xAA5BCF57</td></tr>
<tr><td><strong>Instance</strong></td><td>0x10000001</td></tr>
<tr><td><strong>Comments</strong></td><td><em>See also: </em></td></tr>
</table>
</div>

**RUL 0x10000001**, also known as the **Intersection Solutions RUL** and **RUL1**, is a [RUL File](/rul-file) which defines textures or models for intersections between two different networks.

This is the file which dictates what happens when one network type is drawn over a *different* network (note the use of the word "different"; this is important). Intersections involving only a single network type are handled by the [Individual Network RULs](/individual-network-ruls). The network building engine calculates how network piece(s) are laid, as if no other networks are present. Then it looks to see if there are other network tiles of a different network in the way. If there are, it searches for a solution in this file and thus the intersecting piece(s)' Rules are applied. If no Rules are found for the two different networks to intersect though, it results in an impossible network draw (red line).

## Format

The file is separated into sections by titles in \[brackets\]. Each section contains a title line and a series of rules that define how the two networks being considered interact with each other when they intersect. Individual sets of rules within a section, such as for a particular puzzle piece, are separated by commented lines (beginning with a semi-colon) that generally include a name for the piece.

### Section Title

The section title has the following format:

    [Network1Network2IntersectionSolutions]

**Network1** and **Network2** are the two networks which are being overlapped. Valid network names are:

- *DirtRoad* (aka [RHW](/rhw)),
- *Street*,
- *Road*,
- *OneWayRoad*,
- *Avenue*,
- *GroundHighway*,
- *Highway*,
- *Rail*,
- *LightRail* (aka El-train),
- *MonoRail*

(The EXE also has cases for Pipe, Subway and Powerline)

There must be no spaces or punctuation of any kind in the title. Note the special capitalization used in some of the names.

A note about loading order, the section title for each intersection section needs to have its network names in a proper order, otherwise any rules created under that section may not work at all. For example: *\[OneWayRoadGroundHighwayIntersectionSolutions\]* is a valid section title, but *\[GroundHighwayOneWayRoadIntersectionSolutions\]* is not. So if a set of rules doesn’t seem to be working (and no other rules exist in the section), then this may be something to look closer at.

### Rules

Within each section, following the section title, are sets of Rules grouped by the type of intersection between the two networks being considered. Each set typically consists of a comment line containing the piece or intersection name or condition, such as:

    ; straight road, diagonal rail

or

    ;piece 142

These are then followed by the Rules that apply to this particular puzzle piece or intersection condition. These Rules check the edge values of both networks on the tile, and determine the correct texture to apply to the tile.

The format of these lines is as follows:

    name=Network1MajorTypesFlag,Network2MajorTypesFlag,textureID,rotation,flip

- **Name** is not used by the game, and generally any name is valid. Names may be reused throughout the file, and even within the same section.
- **Network1MajorTypesFlag** and **Network2MajorTypesFlag** are the [Network Flags](/network-flags) for the two networks on the tile. More on this below.
- **textureID** is the [Instance ID](/instance-id) for the texture to be placed on the tile when the conditions described in the two MajorTypesFlags are met. This IID may point to a [S3D](/s3d) file, [SC4Path](/sc4path), or [Exemplar](/exemplar). Where an Exemplar file is referenced, this Exemplar file subsequently references an S3D (or Model) file.
- **rotation** is the rotation of the model or texture to be placed on the tile, values are 0-3.
- **flip** is the flip of the model or texture to be placed on the tile, values are 0 or 1.

The Network Flags used here are in the standard S,E,N,W format. Note that only values of *00* to *04* are valid for RUL 0x10000001 rules. The "blend" values, such as *11* and *13* are not valid for these rules. This is because you cannot create intersections between networks at curves, it must be a straight diagonal or orthogonal section of both networks.

An example set of rules is:

    ; straight road, straight rail
    rot0=0x02000200,0x00020002,0x03010100,0,0
    rot1=0x00020002,0x02000200,0x03010100,1,0

This comes from the *\[RoadRailIntersectionSolutions\]* part of the file, so in this case, *Network1 = Road* and *Network2 = Rail*. As you can see, this set contains two rules, for the two possible ways that a straight road can intersect a straight rail. The first rule covers the case of a N-S road crossing an E-W rail, and the second set covers a E-W road crossing a N-S rail. Note that both rules point to the same *textureID*, and simply rotate it to cover both possible orientations of the two networks.

Note: Some in-game network intersections rely on having various RUL 0x10000001 rules in place in order for them to work. Some intersections/junctions may need two different sets of RUL 0x10000001 rules, that effectively work together for an intersection to work. Some intersections/junctions rely on [RUL 0x10000002](/rul-0x10000002) rules in order to work effectively. Some examples of this can be seen in these files themselves.

### Allowed Overrides Section

The Allowed Overrides Section comes at the end of the file, after all of the Rules sections. This controls what networks may be drawn (in a parallel overlapping fashion) on top of other networks.

If the [Network Flags](/network-flags) are the same for both networks on a given tile, it allows you to replace a tile from the second network mentioned with a tile from the first network mentioned. The only exception to this is that *04* flags are ignored for streets and roads when drawing avenues over them. Presumably, this is a hardcoded exception.

Unfortunately, the rules here in this last section are also read in reverse by the EXE. And because of the hierarchy that exists with the networks, a lower hierarchical network can't replace a higher hierarchical network when actively dragging one network over another. So having *X=Street,Road* won't force Street to replace Road as the Street tool is dragged over a stretch of Road. Rather, *X=Street,Road* will effectively be read as *X=Road,Street* at run-time and thus allow Road to replace Street if the Road tool is dragged over a section of Street.

This section, as originally written looks like:

    [AllowedOverrides]
    1=Road,Street
    2=Avenue,Road
    3=Avenue,Street
    4=Avenue,GroundHighway
    5=Highway,GroundHighway
    6=OneWayRoad,Road

This section has however been significantly expanded by [NAM](/nam) to include the full array of networks.

1.  [Network Specs](/network-specs)
