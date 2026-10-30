---
title: "AVP"
description: ""
published: false
date: '2019-08-09T02:54:46Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2011-06-01T00:24:25Z'
---

## Overview

AVP (Animation View Position) files are used to create small animated props. They are referenced by [ATC](/atc) files and specify the location and size of animation frames within a source [FSH](/fsh). They can specify a variable number of rotations, but only 4 (for props) and 8 (for sprites, i.e. pedestrian animations) are useful.

## Important Points

AVP files and their companion ATC files have some specific requirements and caveats:

- Each ATC file must have a unique set of AVP files or the prop will appear in game as a brown box.
- Multiple ATC files can reference the same source FSH. (Although this will cause incorrect animations in the Reader, they will appear correctly in game.)
- ATC prop rotations are specified in a different order than S3D prop rotations. (This is not a problem for most standalone props, but traffic lights and RR crossings interact with stop points and static props and must be created correctly.)

<figure>
<img src="/images/S3d_vs_atc_rotations.png" title="S3d_vs_atc_rotations.png" />
<figcaption>S3d_vs_atc_rotations.png</figcaption>
</figure>

## Format

AVP files are small files, between 68 and 100 bytes, that specify rotations, frame coordinates, and sizes and anchor references. They are referenced using [ATC](/atc) files.

### File Structure

AVP files consist of a header section (36 bytes), followed by repeating chunks of information containing rotation entries. It has been noted that bytes 10 through 1C may be intended for user data, or are reserved for later use.

*All WORDs and DWORDs are stored in little endian notation.*

00: DWORD - AVP Type Value (always **09ADCD75**)  
04: DWORD - Number Of Rotations (must match byte 20 below)  
08: DWORD - Major Version Number (Always **00000001**)  
0C: DWORD - Minor Version Number (Always **00000001**)  
10: DWORD - Unknown (always **00000000**)  
14: DWORD - Unknown (always **00000000**)  
18: DWORD - Unknown (always **00000000**)  
1C: DWORD - Unknown (always **00000000**)  
20: DWORD - Number Of Rotations (must match byte 04 above). Tells the software how many rotations to expect following this point.  
24+: Rotation Entries (8 bytes each, number of entries must match number of rotations in bytes 04 and 20):

**Repeating Section (Rotation Entries):**  
0: BYTE - Plane Number (Multi-[FSH](/fsh) index number)  
1: BYTE - Source Type (Always **08**, FSH type)  
2: BYTE - First Frame X Offset (Position of the start point on FSH for frame, in pixels into the image.)  
3: BYTE - First Frame Y Offset (Position of the start point on FSH for frame, in pixels into the image.)  
4: BYTE - Frame Width (in pixels)  
5: BYTE - Frame Height (in pixels)  
6: BYTE - Anchor X Coordinate (in pixels)  
7: BYTE - Anchor Y Coordinate (in pixels)  
The number of rotations is variable, but only 4 (for props) and 8 (for sprites, i.e. pedestrian animations) are useful.

### Visual Reference

(Please note the little endian storage of the constants above.)

<figure>
<img src="/images/AVP_format.png" title="AVP_format.png" />
<figcaption>AVP_format.png</figcaption>
</figure>
