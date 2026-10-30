---
title: "Modelling for Networks"
description: ""
published: true
date: '2019-08-04T05:46:35Z'
tags: ["Transit Networks"]
editor: markdown
dateCreated: '2008-05-29T05:48:32Z'
---

Modeling pieces for the [transit networks](/transit-network) in [SC4](/sc4) is, in many regards, a completely different process than modeling buildings, and has more in common with [automata](/automata) modeling. The models have to be designed and exported following very specific guidelines, which need to be followed carefully, or else the model will be completely unusable for transit purposes. So, in order to help those out who are interested in making models for transit networks, I have listed the four most basic requirements below. They apply to all transit models except [bridge](/bridge) pieces. See the [Bridge Moddeling](/tutorial/bridge-modeling) tutorial for the correct specifications for bridges.

## The basic structure of transit models

**The model must consist of a series of segments, fitting within a 16 meter by 16 meter square frame (equivalent to 1 SC4 Tile).** For models covering more than one tile ([puzzle pieces](/puzzle-piece)/interchanges), the game will reassemble these segments into the full model through the use of a specific [IID](/iid) scheme and appropriate entries in the [IntersectionOrdering RUL](/rul-0x10000000) (RUL 0x10000000). Each segment will need to be rendered/exported on its own (without the other pieces present), centered at the "zero point" (x=0, y=0, otherwise the piece will be offset and cannot be [pathed](/path) properly). This is perhaps the most important initial guideline to follow, as if it is not adhered to, the model will be unusable and in order to make it usable, you will have to split the model up after the fact, which can be an extremely time-consuming process.

## Size Restrictions

**The overall model (with all segments combined) can be no larger than 16 SC4 tiles by 16 SC4 Tiles.** This is a limitation of [RUL 0x10000000](/rul-0x10000000). Anything larger will need to be split into multiple pieces.

## True 3-Dimensional Export

**The model must be rendered/exported in True 3D.** As you may know, the standard [BAT](/bat) export procedure reduces the model to a series of isometric faces, which are assembled in composite by the game to form the building/prop/etc. However, the game does not handle transit models in the same manner, and when exported as per the normal BAT process, they will look correct from one angle, but will look incorrect from any others. There are two methods to get around this:

a\) Temporarily replace the BuildingMill.ms script (for gmax, this will be found in your gmax\gamepacks\BAT\scripts folder) with the modified one, which will force the BAT to export in True 3D instead of isometric composites. b) Export the model as a .3ds mesh file, which can be directly imported into the Reader, skipping the rendering process altogether. This is more difficult to do with [Gmax](/gmax) (since it cannot export this format), but it is possible from 3DS Max, Milkshape3D or from the free, open-source program [Blender](http://www.blender.org).

## Polygon Count Limit

**The model must have fewer than 500-600 polygons.** True 3D models are actually higher in poly count upon arriving in game than standard BAT models, as they haven't been reduced to isometric faces, and thus, are more taxing on the game and system resources. If this limit is exceeded, pieces of the model will disappear when it is placed in game, or, in some cases, the game can crash outright. Thus, the model needs to be as simple as possible--Planes are the preferred basic objects to use when creating transit models, as they will hide unnecessary faces.

If there's something extra that you really just have to have on the model, it can be rendered separately through the standard BAT process (remember to switch back to your old BuildingMill.ms file beforehand), turned into a Prop and added to the piece via [Type21](/type21) (T21) [Exemplar](/exemplar).

## Ground-Level Models

Models for ground-level puzzle pieces are actually produced directly in the Reader (with the Vert tab) and not in the BAT, and consist of nothing but a 4-polygon flat plane with textures applied to them. All 3-dimensional detail for ground-level puzzle pieces is best added through T21 Exemplar.
