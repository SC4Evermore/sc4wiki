---
title: "Diagonal Bridge Enabler"
description: ""
published: false
date: '2019-08-04T22:57:14Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2016-02-10T14:31:26Z'
---

## Introduction to the DBE

The NAM Diagonal Bridge Enabler is an additional plugin or mod intended for advanced users, containing a special "temporary" file. This modifys the game's transit network slope and terrain parameters, allowing for the construction of otherwise impossible diagonal bridges. Coupled with starter pieces enabling several different styles of diagonal bridges.

## Screenshots

![](/_files/images/namdocdbeteaser1.jpg) ![](/_files/images/namdocdbeteaser3.jpg)

![](/_files/images/namdocdbeteaser2.jpg) ![](/_files/images/namdocdbeteaser4.jpg)

## Contents/Instructions

The Diagonal Bridge Enabler contains just two files: the main file DiagonalBridgeEnabler.dat, and DiagonalBridgeEnabler_Locale_english.dat (which contains description strings for pieces and menu icons). There are temporary files designed only to be used when you wish to construct diagonal bridges. It is recommended you take the entire ~Diagonal Bridge Enabler folder and drop it into your Plugins, making sure to remove it when you are finished constructing your diagonal bridges. The file does the following:

- Lowers the sea level to 0, effectively draining any in-game bodies of water in an opened city.
- Forces the Road, One-Way Road, Rail and RealHighway networks to be completely level, allowing them to be dragged across the drained bodies of water.
- Enables buttons in the Road and Rail menus, containing Diagonal Bridge starter pieces and Waterbridge Viaduct puzzle pieces.
- Adds pylon exemplars to the Rail and RealHighway networks.

Upon opening your city tile with the ~Diagonal Bridge Enabler folder installed, you will notice all game water has been drained from the map, and your terrain will have dramatically shifted color (with default Maxis terrain, it will appear that your city is now in a desert). If you attempt to drag the Road, One-Way Road, Rail or RealHighway networks, you will notice that they stay on a level plane and can be dragged across the chasms where the waterways once were in your city. You can use this to create diagonal, curving and even neighbor connecting bridges with these networks with Maxis' default pylons (see [here](http://sc4devotion.com/forums/index.php?topic=11555.0) for more information). Removing the temporary files when you are done will restore the terrain, refill your bodies of water, and return network slopes to their regular setting (either the defaults or whatever slope mod you may have installed).

<figure>
<img src="/_files/images/namdocdbereadme0.jpg" title="NAMDocDBEReadme0.jpg" />
<figcaption>NAMDocDBEReadme0.jpg</figcaption>
</figure>

However, these default pylon bridges may leave something to be desired from a visual, aesthetic standpoint. Thus, the DBE also enables a set of options, designed to emulate the look and feel of traditional SC4 water bridges. The options available include the following:

## Diagonal Bridges (under the Roads Menu)

- Road Level Bridge (drag with Road network)
- Road Lars Bridge (drag with Road network)
- Road Undertruss Bridge (drag with Road network)
- One-Way Road Level Bridge (drag with One-Way Road network)
- One-Way Road Lars Bridge (drag with One-Way Road network)
- One-Way Road Undertruss Bridge (drag with One-Way Road network)
- Avenue Level Bridge (drag with RealHighway network)
- Avenue Undertruss Bridge (drag with RealHighway network)
- Rail Level Bridge (drag with Rail network)
- Rail Undertruss Bridge (drag with Rail network)
- Ground Highway Bridge Standard (drag with RealHighway network)

These items under this button are all starter piece items, from which one drags the network listed above from the end of a puzzle piece.

First, you'll want to drag your network across the drained waterway as shown below:

<figure>
<img src="/_files/images/namdocdbereadme1.jpg" title="NAMDocDBEReadme1.jpg" />
<figcaption>NAMDocDBEReadme1.jpg</figcaption>
</figure>

For the continuation of the ground roadway, you'll want to have a space between the bridge and the ground roadway as follows, and place the starter piece you wish to use on top in the following manner (with the arrows facing toward the bridge):

<figure>
<img src="/_files/images/namdocdbereadme2.jpg" title="NAMDocDBEReadme2.jpg" />
<figcaption>NAMDocDBEReadme2.jpg</figcaption>
</figure>

This will convert part of the default pylon bridge.

<figure>
<img src="/_files/images/namdocdbereadme3.jpg" title="NAMDocDBEReadme3.jpg" />
<figcaption>NAMDocDBEReadme3.jpg</figcaption>
</figure>

To continue converting the rest, simply click the network tool every few tiles along the path of the bridge, and it'll convert (tip: follow the pylons--it may be rather tricky at times because of the height of the pylons). To ensure the new pylons remain stable, ensure that you have finished the full bridge before continuing.

<figure>
<img src="/_files/images/namdocdbereadme4.jpg" title="NAMDocDBEReadme4.jpg" />
<figcaption>NAMDocDBEReadme4.jpg</figcaption>
</figure>

Once you get to the other side, use a second starter piece, placing a gap between your bridge and ground roadway. This will seal in the override and prevent the ground roadway on the other side from turning into a bridge as well. If any bridge pieces remain after the starters are in place, you can simply click with the appropriate network tool on them. This will revert them to the regular network.

<figure>
<img src="/_files/images/namdocdbereadme5.jpg" title="NAMDocDBEReadme5.jpg" />
<figcaption>NAMDocDBEReadme5.jpg</figcaption>
</figure>

Now that you've built your bridge, you can now close the game, take the ~Diagonal Bridge Enabler (Temporary Files) folder out of your Plugins, and reopen the game. Your terrain and slope settings will be restored back to their previous settings, and the water will return:

<figure>
<img src="/_files/images/namdocdbereadme6.jpg" title="NAMDocDBEReadme6.jpg" />
<figcaption>NAMDocDBEReadme6.jpg</figcaption>
</figure>

Since the techniques involved here do not support dual-tile networks, the Avenue and Ground Highway bridges are based off the RealHighway network, to keep the capacities up. Dragging a "shared tile" RealHighway setup is necessary in order for these to work.

<figure>
<img src="/_files/images/namdocdbereadme7.jpg" title="NAMDocDBEReadme7.jpg" />
<figcaption>NAMDocDBEReadme7.jpg</figcaption>
</figure>

<figure>
<img src="/_files/images/namdocdbereadme8.jpg" title="NAMDocDBEReadme8.jpg" />
<figcaption>NAMDocDBEReadme8.jpg</figcaption>
</figure>

While the pylon techniques do allow for curving, intersecting and neighbor connecting functionality, these draggable bridge items are currently intended for strictly diagonal usage--no curving or intersecting. Attempting to curve or intersect one of these bridges from their intended diagonal trajectory will result in the override breaking, leaving behind a default pylon bridge.

## Diagonal Viaduct Rail Waterbridges (under the Rails menu)

- Diagonal Railroad Viaduct with Long Support
- Diagonal Railroad Viaduct Truss Bridge Start/End
- Diagonal Railroad Viaduct Truss Bridge (without supports)
- Diagonal Railroad Viaduct Truss Bridge with Long Support

These pieces allow for the construction of modular, puzzle piece-based Elevated Heavy Rail Viaduct Truss Bridges, designed to work with the NAM's Elevated Heavy Rail Viaducts. Their appearance will conform to whatever texture style you chose for the Rail Viaducts (Gray Brick, Brown Brick, or Red Brick) when you installed the NAM. To use these, simply drag out a diagonal default pylon bridge with the Rail network over your drained waterway, and plop the puzzle pieces over top.

<figure>
<img src="/_files/images/namdocdbereadme9.jpg" title="NAMDocDBEReadme9.jpg" />
<figcaption>NAMDocDBEReadme9.jpg</figcaption>
</figure>

A finished product:

<figure>
<img src="/_files/images/namdocdbereadme10.jpg" title="NAMDocDBEReadme10.jpg" />
<figcaption>NAMDocDBEReadme10.jpg</figcaption>
</figure>

## Dependencies

The following files are required in order for the Diagonal Bridge Enabler to function:

- Network Addon Mod, Version 30 with Essentials r132 (or later)

Note: In order to make Avenue and Highway bridges, you must install the base RHW-2 L0 network for RealHighway. The following files (from the NAM) must exist in your plugins folder:

- Network Addon Mod\NetworkAddonMod_Controller.dat
- Network Addon Mod\NetworkAddonMod_BridgeSupport.dat
- Network Addon Mod\NetworkAddonMod_IndividualNetworkRULs.dat
- Network Addon Mod\Real Highway Mod\L0\RealHighway_L0_RHW-2.dat

## Compatibility

The DBE is only compatible with SimCity 4 "Rush Hour" or SimCity 4 Deluxe (including copies downloaded through Steam). The Version 1.1.638 patch is highly recommended, and can be found in the EA/Maxis Support section at SimCity 4 Devotion. Please read the instructions on the site to ensure that you download the correct version of the patch for the region in which you purchased your copy of the game (the Steam and other online "digital" versions usually come pre-patched). Attempting to use this mod with other versions of SimCity 4 will cause the game to instantly crash upon loading.

## Installation

The DBE files are intended for temporary use, and to facilitate this, simply drop the ~Diagonal Bridge Enabler folder into your Plugins when you're ready to build Diagonal Bridges, and remove it when you're done. Un-Installing: To uninstall the Mod, simply remove the files from the plugins folder. Yes, it's that easy!

## Credits

Developers

- ArkenbergeJoe
- daeley
- memo
- praiodan

Testing

- Blue Lightning
- Chrisim
- jdenm8
- noahclem

Documentation/Packaging

- Tarkus

Special Thanks

- NAM Team and Associates
