---
title: "Network Specs/IntersectionSolutions RUL"
description: ""
published: false
date: '2019-08-04T05:45:28Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-09T12:08:34Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Network Specs/IntersectionSolutions RUL</th></tr>
<tr><td><strong>Name</strong></td><td>RUL Overrides</td></tr>
<tr><td><strong>Format</strong></td><td><a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x0A5BCF4B</td></tr>
<tr><td><strong>Group</strong></td><td>0xAA5BCF57</td></tr>
<tr><td><strong>Instance</strong></td><td>0x10000001</td></tr>
</table>
</div>

This is the file which dictates what happens when one network type is drawn over a different network (note the use of the word "different"; this is important). The network building engine calculates how network piece(s) are laid, as if no other networks are present. Then it looks to see if there are other network tiles of a different network in the way. If there are, it searches for a solution in this file and thus the intersecting piece(s)’ Rules are applied. If no Rules are found for the two different networks to intersect though, it results in an impossible network draw (red line). Format is as follows.

## Maxis' Comments

<font color="green" face="Courier New"> ; format:  
; name=roadMajorTypesFlag,streetMajorTypesFlag,textureId,rotation,flip  
;  
; name is really not used and is just for our reference.  
; the flag byte order is SENW (I think?)  
</font>

## Translation

The file is separated into sections by titles in \[brackets\]. The title has the following format:

<font color="green" face="Courier New">\[***Network1Network2***IntersectionSolutions\]</font>

**Network1** and **Network2** are the two networks which are being overlapped. Valid network names are: DirtRoad, Street, Road, OneWayRoad, Avenue, GroundHighway, Highway, Rail, LightRail (aka El-train), and MonoRail (and some others). There must be no spaces or punctuation of any kind in the title.

A note about loading order, the IntersectionSolutions header for each intersection section needs to have its network names in a proper order, otherwise any rules created under that section may not work at all. For example: \[OneWayRoadGroundHighwayIntersectionSolutions\] header is valid, but the \[GroundHighwayOneWayRoadIntersectionSolutions\] header is not. So if a set of rules doesn’t seem to be working (and no other rules exist in the section), then this may be something to look closer at.

Within each section, there are lines which describe the tile to place in the case where tiles of Network1 and Network2 are placed on top of each other, with the defined RUL edge values. The format of these lines is as follows:

<font color="green" face="Courier New"> ;straight road, diagonal rail  
rot0flip0=0x02000200,0x00030100,0x03010200,0,0</font>

## Format

<font color="green" face="Courier New">name=<font color="black">0x</font><font color="blue">N1s</font><font color="orange">N1e</font>N1n<font color="purple">N1e</font>,<font color="black">0x</font><font color="blue">N2s</font><font color="orange">N2e</font>N2n<font color="purple">N2e</font>,texture/path/ExemplarID,Rotation,Flip</font>

- name = doesn't matter, generally anything is valid
- N1=Network1\<
- N2=Network2
- s,e,n,w = South, East, North, West

Each S/E/N/W holds the RUL edge values for each network, which are:

`00 - no connection`  
`01 - left at 45degree angle`  
`02 - straight`  
`03 - right at 45degree angle`  
`04 – median`

- Texture/PathID/ExemplarID = the InstanceID of the resulting transit tile put in this spot.

Where an [Exemplar](/exemplar) file is referenced, this Exemplar file subsequently references an [S3D](/s3d) (or Model) file.

- Rotation = the rotation of the new transit tile 0-3
- Flip = the flip of the new transit tile 0-1

Note: Some in-game network intersections rely on having various IntersectionSolution rules in place in order for them to work. Some intersections/junctions may need two different sets of intersectionsolution rules, that effectively work together for an intersection to work. Some intersections/junctions rely on the RuleOverrides RUL in order to work effectively. Some examples of this can be seen in these files themselves.

## Allowed Overrides Section

<font color="green" face="Courier New">\[AllowedOverrides\]  
1=Road,Street  
2=Avenue,Road  
3=Avenue,Street  
4=Avenue,GroundHighway  
5=Highway,GroundHighway  
6=OneWayRoad,Road  
</font>

This controls what networks may be drawn on top of other networks. Unfortunately, the rules here in this last section are also read in reverse by the EXE. And because of the hierarchy that exists with the networks, a lower hierarchical network can't replace a higher hierarchical network when actively dragging one network over another (in a parallel overlapping fashion). So having X=Street,Road won't force Street to replace Road as the Street tool is dragged over a stretch of road. Rather, X=Street,Road will effectively be read as X=Road,Street at run-time and thus allow Road to replace Street if the Road tool is dragged over a section of Street.
