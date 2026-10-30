---
title: "Network Specs/INI Network & Bridges"
description: ""
published: true
date: '2019-08-04T05:45:29Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-11T20:35:25Z'
---

This file covers items related to the [Network INI](/network-ini) file and [Bridge RUL](/bridge-rul) files. Not all aspects of these files will be covered though.

- INI Network file – *0x00000000/8A5971C5/8A5993B9*
- Bridge RULs – *0x0A5BCF4B/AA5BCF57/00001000* to *0x0A5BCF4B/AA5BCF57/000010##*

<!-- -->

- Note: The game originally only came with five Bridge RUL files. Other Bridge RULs other than the original five have been known to be valid though, hence where there is '##' at the end.

## Remapping

### Paths

<font face="Courier New"> \[UK path remapping\]  
<font color="green"> ; Format:  
;  
; <anything> = <match-id>, <match-mask>, <new-id>, <add-mask>  
</font> 1 = 0x09201000,0xFFFFF000,0x09209000,0x00000FFF  
1 = 0x09209000,0xFFFFF000,0x09201000,0x00000FFF  
</font>

This section is mostly used in conjunction with the IntersectionOrdering RUL file. Basically, this section is used to replace particular path file or sets of path files at run-time for any given in-game tiles. Each line contains 2 main parts.

<font face="Courier New"> 1 = 0x09201000,0xFFFFF000,0x09209000,0x00000FFF  
</font>

This says that any Path files with IDs of *0x09201###* be replaced with the Path files that exist in *0x09209###*, for UK (or left hand side) driving orientated games. The "F"s denote masking of an ID. These, as too the IIDs, can be changed and/or shifted over, but in practice are not. The following would also be a valid and work (assuming the Path files are in place for these):

<font face="Courier New"> 1 = 0x09210000,0xFFFF0000,0x0929000,0x0000FFFF  
</font>

### Texture Remapping

This particular section controls the texture remapping of an item when the network is being drawn. Or in other words, the **Preview** of an ordinary in-game tile of the network before you release the mouse button. This does not cover Bridges and interchange items.

## Bridges

### Exemplar Files

Bridges are a little different from other network items in the game. Unlike normal network aspects, Bridges are first called from the network INI file.

<font color="green" face="Courier New"> \[RoadBridgeExemplars\]  
; 0x2821ED93  
1 = 0x6534284a, 0xa82ca30f, 0x00000001, level road bridge  
2 = 0x6534284a, 0xa82ca30f, 0x00000002, raised road bridge  
3 = 0x6534284a, 0xa82ca30f, 0x00000003, undertruss road bridge  
4 = 0x6534284a, 0xa82ca30f, 0x00000005, wooden covered road bridge  
5 = 0x6534284a, 0xa82ca30f, 0x00000006, medium suspension road bridge  
6 = 0x6534284a, 0xa82ca30f, 0x00000007, stone arch road bridge  
7 = 0x6534284a, 0xa82ca30f, 0x00000008, small steel arch road bridge  
8 = 0x6534284a, 0xa82ca30f, 0x00000009, cantilever truss road bridge  
9 = 0x6534284a, 0xa82ca30f, 0x0000000a, overdeck truss road bridge  
</font>

This section here is the starting point for bridges. Each of the different networks that have bridges contains entries similar to this.

#### Format

<font color="green" face="Courier New">\[RoadBridgeExemplars\]</font>

This is the header for this section, and the network names are engine specific.

<font color="green" face="Courier New"> 1 = 0x6534284a, 0xa82ca30f, 0x00000001, level road bridge</font>  
Number = TypeID, GroupID, InstanceID, Name  

- Number – These should be unique, as they can and are used as a point of reference in the Bridge RUL files.
- Name - insignificant. Name can be anything.
- Type/Group/Instance IDs - this is an actual Bridge Parent-Exemplar file that this is pointing to. This referenced Bridge Parent-Exemplar file then follows on to reference Child-Exemplar files. These Child-Exemplar files not only fall under the [Group ID](/group-id) specific format, but also a specific [Instance ID](/instance-id) format as well (which is believed to subsequently be controlled by the INI file itself, namely the section under Shadow Remappings).

If you have a look at the <font color="green">Level_Road_Bridge</font> Exemplar file (find the Exemplar file using the above referenced TGI ID, level road bridge), you’ll notice it contains many properties, among them the following properties:

- 0x482CB443  
- 0x482CB445  
- 0x482CB449  

Not all of these three will be in every Bridge Exemplar.

These properties contain the pointers, or InstanceIDs, of the Child-Exemplar files mentioned above. Essentially, the INI Network file and the referenced Bridge Parent-Exemplar file, controls the "ability" to actually build a bridge (Hint: A bridge can be built, carry commuters, & still not be visible. This would indicate a GroupID and/or InstanceID problem with the files involved, and/or possibly a S3D file problem). The Bridge RUL files are only supplementary after this; most of the bridges work this way.

### RUL files

[Bridge RULs](/bridge-rul) have a format all to themselves, and are very different from all the other RULs. The Bridge RULs have their format within them.
