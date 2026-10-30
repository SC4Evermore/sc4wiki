---
title: "Network Specs/RuleOverrides RUL"
description: ""
published: false
date: '2019-08-04T05:45:27Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-09T11:46:50Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Network Specs/RuleOverrides RUL</th></tr>
<tr><td><strong>Name</strong></td><td>RUL Overrides</td></tr>
<tr><td><strong>Format</strong></td><td><a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x0A5BCF4B</td></tr>
<tr><td><strong>Group</strong></td><td>0xAA5BCF57</td></tr>
<tr><td><strong>Instance</strong></td><td>0x10000002</td></tr>
</table>
</div>

Probably the simplest [RUL](/rul) file in format, but hardest to grasp in practice. This file works by saying that if two textures are aligned next to each other like this (it also works with models):

If **Texture1** is next to **Texture2** is True,

Then **Texture1a** replaces **Texture1** and **Texture2** replaces **Texture2a**

For example:

<font color="green" face="Courier New, green" > 0x03001c00,2,1,0x0324fd00,2,1=0x03aa6600,3,0,0x0324fd00,2,1 </font>

## Format

    ID1,Rot1,Flip1,ID2,Rot2,Flip2=ID1a,Rot1a,Flip1a,ID2a,Rot2a,Flip2a

These particular rules are very powerful, since one line makes them work in all four cardinal orientations. The left/right perspective is not set in stone to a cardinal direction. Rather, the right side of Tile1 has to border the left side of Tile2.

Having zeros in the ID1a and ID2a spots causes a bad draw (red line). This is to keep things from being constructed which don't look right, but still conform to all the other Rules.

## Notes

The RuleOverrides RUL is used to fix bugs and replace intersections/junctions and/or set-ups for whatever reason. They are also used to enforce, and/or follow on from, a set of rules from another RUL file (like the IntersectionSolutions RUL) to enhance a junction. One such example of this is the Avenue-to-Highway Transition. Note that the RulOverrides rul can make impossible junctions possible, but doing so may require quite the number of rules.
