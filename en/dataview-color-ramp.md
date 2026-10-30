---
title: "DataView:Color Ramp"
description: ""
published: true
date: '2021-03-21T17:07:06Z'
tags: []
editor: markdown
dateCreated: '2021-03-21T16:37:33Z'
---

**DataView: Color Ramp** is a property associated with [Data Views](/data-view) and controls the color patterns and progressions overlayed on the map. Desc: Color progression to use for data

Format: array of integers between 0 and 10,000,000 2d array of integers (2 col, unknown max rows). First column is the “breakpoint” – dec 0-255 hex 0-ff. second column is color value – 0xAARRGGBB

Default values: 0x00000000 0xff000000 0x00000040 0xff3f3f3f 0x0000000080 0xff7f7f7f 0x000000c0 0xffbfbfbf 0x000000ff 0xffffffff

If color is same on two consecutive lines, then the breakpoint for the first identical instance marks the start of that color and the breakpoint for second identical instances marks the end of that color. All data values within this range will show the same color. All other breakpoints are “blended” and colors will automatically be created for all values in between.
