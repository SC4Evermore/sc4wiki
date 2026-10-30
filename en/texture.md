---
title: "Texture"
description: ""
published: false
date: '2019-08-04T05:40:54Z'
tags: ["Modding", "Lot Editor", "Building Architect Tool"]
editor: markdown
dateCreated: '2008-09-21T10:12:54Z'
---

**Textures** are used widely by [SimCity 4](/simcity-4) in a variety of ways, and the meaning of the word can vary drastically depending on the context. The one consistent definition is that a texture is an image. The [Texture Index](/texture-index) has been created to help coordinate use of textures throughout the community, and avoid texture conflicts.

## Textures In Game

Because SimCity 4 must represent a 3-dimensional environment (the city, with it's terrain, buildings, etc.) in a 2-dimensional plane (your computer screen), it is necessary to have image files that can be applied to the various in-game objects that look correct when viewed on a screen. These textures are [FSH](/fsh) files, and are created for any game object in a variety of zooms and rotations to account for the different camera angles available in-game. Every visible object in the game, whether building, prop, road, terrain, etc., must have textures associated with it, or it will not be seen.

## Textures in BATting

When BATting, it is common to discuss the texturing of a building (or prop, or tree, etc.) This use of the word *texture* is different from above, as these textures are regular images that are applied to the various surfaces of the object being designed. Think of this as similar to wallpapering a building, or applying a skin over a skeleton. These textures are inherently bound to the skeleton of the object during the rendering process, with the result being the FSH files that are actually displayed in-game. Files used as textures in BATting can be any sort of normal graphics file. These textures are not game dependencies, since they become part of the model file during rendering.

## Textures in LOTting

Textures used in [Lots](/lot) are yet another meaning of the word. In this case, the textures are FSH files, however they are applied to the ground plane of the lot during the lot editing process. They can consist of either [base textures](/base-texture) or [overlay textures](/overlay-texture). Unlike BATting, these textures are not graphically bound to the Lot, but are instead listed in an [exemplar](/exemplar), and called every time the lot appears in-game. Consequently, Lot textures are a common [dependency](/dependency), and several texture packs have been created by various custom content creators.

## Network Textures

Textures are also used to define the appearance of transportation networks. Like Lots, these textures are applied to the ground plane, but instead of being on the ground plane of a Lot, they are on the ground plane of the terrain itself. Textures used for networks often appear in Lots, particularly transit enabled lots, such as train stations or toll booths, to maintain continuity of appearance across a transportation Lot. The placement of a particular texture in a particular location is governed by various network files. A tutorial in creating Network Textures is available [here](/tutorial/creating-textures).

## Terrain Textures

The final major use of textures in SimCity 4 is for terrain. These operate similar to Network Textures in that they are applied to the ground plane of the city, and are made up of FSH files. Because terrain textures cover such a large surface area (the entire city tile), and must respond to the shape of the sometimes complex 3D landscape to which they are applied, there are several files and variables that control their placement.
