---
title: "HID"
description: ""
published: true
date: '2019-08-04T05:43:04Z'
tags: ["Transit Modding"]
editor: markdown
dateCreated: '2009-01-20T18:10:12Z'
---

**HID** stands for hex-ID. It is used in [RUL 0x10000000](/rul-0x10000000), to identify puzzle pieces and to link them to Rotation Rings, and then Icons.

In these lines, the bold numbers are HIDs:

`RotationRing = `**`5000, 5001, 5002, 5003, 5004, 5005, 5006, 5007`**` ;RHW-4 Starter Piece`  
`AddTypes = `**`5010, 5011, 5012, 5013, 5014, 5015, 5016, 5017`**` ;RHW-6S Starter`

`[HighwayIntersectionInfo_0x0000`**`5000`**`]`

They are not limited to having 8 IDs ina line, and several pieces have 16 in a line. The first four digits are the main puzzle piece and then the numbers after are usually rotations/flips of the first. Each line down is the pieces that are for plopping when TAB/Shift TAB is pressed after clicking the icon

To link puzzle pieces to an icon, the button ID will be 0x6A47#### , where \# is the HID.

So the button ID for the piece above (RHW-4 Starter) would be 0x6A47**5000**.

*See also: [RUL 0x10000000](/rul-0x10000000)*
