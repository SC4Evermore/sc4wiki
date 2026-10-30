---
title: "Power Simulator Subfile"
description: ""
published: true
date: '2019-08-10T02:39:54Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T02:39:54Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Power Simulator** file within [Savegame](/savegame) files. This file has [Type ID](/type-id) *0990C005*. This particular file has not been well studied, but some things are known from preliminary investigations. In cities with power plants, there are numbers at the beginning of the file with power capacity and usage (some repeated several times for some reason). The impact of power neighbor deals on this file has not been researched.

## Specification

Following the beginning section of the file are DWORDs with the width and height of the current map. An array of integer values follows, mapping out power consumption tile by tile. In a small test city, adding up each integer on the bitmap totaled the city's power consumption since there were no deals being made. This is the easiest way for the power simulator to track power usage in a city and where the power is being used. There is also another section at the bottom of the file which seems to be another array which may map out power lines/powered areas of the map.
