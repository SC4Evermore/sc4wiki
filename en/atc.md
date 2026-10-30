---
title: "ATC"
description: ""
published: true
date: '2019-08-09T02:54:46Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2011-06-01T00:22:08Z'
---

## Overview

ATC (Animated Texture Collections) files are used to create small animated props. They are referenced by prop exemplars via [RKT0](/resource-key-type#rkt0) properties, but the animations share more in common with isometric models referenced by [RKT1](/resource-key-type#rkt1) properties.

## Important Points

ATC files and their companion [AVP](/avp) files have some specific requirements and caveats:

- Each ATC file must have a unique set of AVP files or the prop will appear in game as a brown box.
- Multiple ATC files can reference the same source [FSH](/fsh). (Although this will cause incorrect animations in the Reader, they will appear correctly in game.)
- ATC prop rotations are specified in a different order than S3D prop rotations. (This is not a problem for most standalone props, but traffic lights and RR crossings interact with stop points and static props and must be created correctly.)

<figure>
<img src="/_files/images/s3d-vs-atc-rotations.png" title="S3d_vs_atc_rotations.png" />
<figcaption>S3d_vs_atc_rotations.png</figcaption>
</figure>

## Format

ATC files are small files, always 48 bytes, that group together [AVP files](/avp), a [FSH](/fsh) image used as a frame source, and specify a number of frames. They also serve as the model reference for props, referenced using a [RKT0](/resource-key-type#rkt0) property or one state of a [RKT4](/resource-key-type#rkt4) property.

### File Structure:

ATC files have the following file structure:

*All WORDs and DWORDs are stored in little endian notation.*

00: DWORD - ATC Type Value (always **29A5D1EC**)  
04: DWORD - Source FSH Type Value (always **7AB50E44**)  
08: DWORD - Source FSH Group Value (usually **2A2458F9**, others may be valid but not tested)  
0C: DWORD - Source FSH Instance Value  
10: DWORD - AVP Type Value (always **09ADCD75**)  
14: DWORD - AVP Group Value (always **2A2458F9**)  
18: DWORD - Zoom 1 AVP Instance Value (usually **00000000** Animations are generally not visible at zooms 1 and 2)  
1C: DWORD - Zoom 2 AVP Instance Value (usually **00000000** Animations are generally not visible at zooms 1 and 2)  
20: DWORD - Zoom 3 AVP Instance Value  
24: DWORD - Zoom 4 AVP Instance Value  
28: DWORD - Zoom 5 AVP Instance Value  
2C: DWORD - Number Of Frames  

### Visual Reference:

(Please note the little endian storage of the constants above.)

<figure>
<img src="/_files/images/atc-format.png" title="ATC_format.png" />
<figcaption>ATC_format.png</figcaption>
</figure>
