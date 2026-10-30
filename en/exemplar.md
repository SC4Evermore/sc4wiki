---
title: "Exemplar"
description: ""
published: true
date: '2019-08-04T05:40:29Z'
tags: ["Modding"]
editor: markdown
dateCreated: '2008-08-31T11:00:45Z'
---

**Exemplars** are some of the most common and most important files in terms of game functionality, and some understanding of them is necessary to undertake most modding projects. They affect buildings, the game's internal simulators, tuning parameters, and transit networks. All exemplars are a collection of properties, and can be represented in text - as such they are easily read using ILive's [Reader](/reader). Many other programs are also able to read exemplars, but tend to only open the ones they were specifically designed to edit. All exemplars have the [Type ID](/type-id) **0x6534284A**.

See the [exemplar properties](/exemplar-properties) page for a full list of known and unknown properties.

The [SimCity (2013)](/simcity-2013) equivalent is the [PROP](/prop-file-format) file format

Exemplars can be grouped as "children" to a Parent [Cohort](/cohort), which will cause them to inherit certain properties from the parent cohort. This is particularly useful if you have a category of exemplars that you want to share common properties, in which case you can assign these properties to a cohort, and then assign the exemplars to this cohort. This also helps reduce the size of an exemplar by shifting some of it's data to the cohort file.

## Exemplar Format

All exemplars share the same file format, which is also used by cohorts. The format is defined by a descriptive header containing the exemplar's file type, [TGI](/type-group-instance), and property count. This is followed by the data of the properties themselves. The full specification can be found [here](/exmp).

## Encoding Issue in the Aspyr Port

The Mac Aspyr port of SimCity 4 is known to have issues with certain exemplar files that are encoded in a particular way. If such afflicted exemplar files are among the plugins, it will cause the game to freeze with an infinitely spinning cursor, upon unpausing the game. It is the only issue known to cause this exact problem.

The problematic exemplar files are those that contain Float32 properties that are encoded in property format 0x80 (for multiple values) *and* hold a single value (Rep 1). These Float32 properties need to be re-encoded to format 0x00 (single value) by changing the Rep value from 1 to 0, in the Reader. Also note that not every such property causes issues, but a more specific rule is not known. It is assumed that a subset of property IDs supports the single-value format only, while the rest supports both formats. If in doubt, use the single-value format or compare with other properties of the same ID that are known to function properly (e.g. those in the SC4 game files).

The problem is usually simple to fix, but it is not always easy to find those properties if a plugin contains many exemplar files.

## Exemplar Types

The **Exemplar Type** is one of the properties of an exemplar, and is used for grouping exemplars into similar categories. Exemplars are often referred to by their type, using the T## terminology, for example T21 exemplars. Note that these types are two-digit hex numbers. Some of the types listed below are network-related [Model Exemplars](/model-exemplar).

| Type | Use |
|----|----|
| 00 | The use of T00 exemplars is relatively unknown. |
| 01 | Tuning Exemplars. These control various game properties such as transit network slopes. |
| 02 | Building Exemplars. These contain properties related to buildings. |
| 03 | RCI Exemplars. |
| 04 | Developer Exemplars. |
| 05 | Simulator Exemplars. These are among the most critical to game functionality, and include among them the Demand Simulator and the [Traffic Simulator](/traffic-simulator). |
| 06 | Road Exemplars. These are generally used for tunnel entrance models. |
| 07 | Bridge Exemplars, which are used to specify bridge properties. |
| 08 | Misc Network Exemplars. |
| 09 | Unknown |
| 0A | Rail Exemplars. |
| 0B | Highway Exemplars, used to reference transit models. They are among the most important exemplars used in the transit-modding world. Virtually all [NAM](/nam) Puzzle Pieces, as well as draggable model-based functionality, as exemplified by the [High Speed Rail](/high-speed-rail) mod, use Type 0B exemplars. |
| 0C | Power line Exemplars. |
| 0D | Terrain Exemplars. |
| 0E | Ordinance Exemplars. |
| 0F | Flora/Fauna Exemplars. |
| 10 | LotConfiguration and Building Exemplars, and are used to specify the location of props, textures and buildings on Lots, along with other properties. Type 10 Exemplars for plopped buildings are stored in a city's [Savefile](/savegame) upon save. |
| 11 | Foundation Exemplars. |
| 13 | Lighting Exemplars. |
| 15 | LotRetainingWall Exemplars. |
| 16 | Vehicle Exemplars, used to reference automata. |
| 17 | Pedestrian Exemplars, used to reference pedestrian automata. |
| 18 | Aircraft Exemplars. |
| 1E | Prop Exemplars. |
| 1F | Construction Exemplars. |
| 20 | Automata Tuning Exemplars. |
| 21 | Network Lots, often referred to by the name [T21](/type21) Exemplars. They are used to add props rendered in [BAT](/bat) (isometric) to [networks](/transit-network), such as traffic lights and lamp posts. These exemplars differ from Lot Exemplars (T10) in that they don't allow for base or overlay textures, and obviously can't be [Transit Enabled](/transit-enabled). |
| 22 | Disaster Exemplars. |
| 23 | DataView Exemplars. |
| 24 | Crime Exemplars. |
| 25 | Audio Exemplars. |
| 27 | God Mode Exemplars. |
| 28 | Mayor Mode Exemplars. |
| 2A | Trend Bar Exemplars. |
| 2B | Graph Control Exemplars. |
