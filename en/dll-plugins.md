---
title: DLL Plugins
description: ''
published: true
date: '2026-11-01T12:17:13.660Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:17:13.660Z'
---

<!-- path: dll-plugins | title: DLL Plugins | tags: DLL Plugins, Plugins, Customizing the Game -->
A **DLL plugin** is a plugin for [SimCity 4](/simcity-4) that contains program code instead of game data. DLL plugins can fix bugs, add features and give modders new possibilities that normal [plugins](/plugins) cannot. Most of them are published on GitHub, often together with a [Simtropolis](/Simtropolis) page and an entry in [SC4Pac](sc4pac)

Most DLL plugins need the digital release of SimCity 4 (version 1.1.641) on Windows. A DLL is usually installed in the top level of a Plugins folder, not in a subfolder. Many DLL plugins can also be installed with the sc4pac package manager.

## gzcom-dll

Most DLL plugins are built with [gzcom-dll](https://github.com/SC4SDK/gzcom-dll), an open source C++ library for SimCity 4. The game is made of components that use a system called GZCOM. When the game starts, it loads the DLL files in the Plugins folder and asks each one for a GZCOM director. Through that director, a DLL can react to game events and use the classes and functions of the game. The SC4 Extra Cheats.dll uses the same system.

[simmaster07](/people/simmaster07) started gzcom-dll in 2012 and did most of the early work in 2016. Since 2023, [Null 45](/people/null-45), [CasperVg](/people/caspervg) and other modders have added many more game interfaces to it. The library is licensed under the LGPL 2.1. Null 45 and CasperVg also publish templates for starting a new DLL plugin, [sc4-gzcom-dll-template](https://github.com/0xC0000054/sc4-gzcom-dll-template) and [sc4-dll-template](https://github.com/caspervg/sc4-dll-template/), respectively.

## Fixes and performance

| Plugin | Author | Description |
|----|----|----|
| [SC4Fix](/plugin/sc4fix) | [simmaster07](/people/simmaster07) | Third-party patches for bugs in the game |
| [NAM DLL](/plugin/nam-dll) | [NAM Team](/network-addon-mod) | Improves how the game works with the Network Addon Mod |
| [CPU Options DLL](/plugin/sc4-cpu-options) | [Null 45](/people/null-45) | Sets the CPU core use and priority of the game |
| [Startup Performance Optimization DLL](/plugin/sc4-dbpf-loading) | Null 45 | Speeds up the plugin loading when the game starts |
| [Region Thumbnail Fix DLL](/plugin/sc4-thumbnail-fix-dll) | [memo](/people/memo) | Fixes gaps in region view thumbnails at large screen sizes |
| [Transparent Texture Fix DLL](/plugin/transparent-texture-fix-dll) | memo | Fixes the underground view bug on lots with overlay textures |

## Graphics and camera

| Plugin | Author | Description |
|----|----|----|
| [SCD3D11](/plugin/scd3d11) | [CasperVg](/people/caspervg) | A Direct3D 11 renderer that replaces the DirectX 7 renderer of the game |
| [scvk](/plugin/scvk) | aspctt | A Vulkan renderer for the game |
| [SCGL](/plugin/scgl) | simmaster07 | An OpenGL 3 renderer for the game |
| [Graphics Options DLL](/plugin/sc4-graphics-options) | Null 45 | Sets the game's rendering mode and resolution options |
| [Disable FPS Limits](/plugin/sc4-disable-fps-limits) | CasperVg | Removes the frame rate limits at each simulation speed |
| [3D Camera DLL](/plugin/sc4-3d-camera-dll) | memo | Adds cheat codes to change the camera angles freely |
| [SC4-ModernCamera](/plugin/sc4-moderncamera) | Rj Simas | A mouse-controlled camera like modern city builders |

## Interface and tools

| Plugin | Author | Description |
|----|----|----|
| [Submenus DLL](/plugin/submenus-dll) | memo | Adds submenus to the building menus of the game |
| [Query UI Extensions DLL](/plugin/sc4-query-ui-hooks) | Null 45 | Extends the query tool UI of the game |
| [Data View Extensions DLL](/plugin/sc4-data-view-extensions) | Null 45 | Extends the game's data views |
| [SC4 Plop and Paint](/plugin/sc4-plop-and-paint) | CasperVg | An in-game panel to plop lots and paint props and flora |

## Frameworks for modders

These plugins mainly give other mods and DLLs new possibilities. Players usually install them because another mod needs them.

| Plugin | Author | Description |
|----|----|----|
| [Resource Loading Hooks DLL](/plugin/sc4-resource-loading-hooks) | Null 45 | Allows DLLs to modify resources as the game loads them |
| [More Building Styles DLL](/plugin/sc4-more-building-styles) | Null 45 | Allows the game to use more than 4 building styles |
| [Lua Extensions DLL](/plugin/sc4-lua-extensions) | Null 45 | Adds new functions for the game's Lua scripts |
| [Lua Sandbox DLL](/plugin/sc4-lua-sandbox-dll) | memo | Blocks unsafe Lua functions that mods could use |
| [More Demand Info DLL](/plugin/sc4-more-demand-info) | Null 45 | Adds game variables with more RCI demand information |
| [Custom Budget Departments DLL](/plugin/sc4-custom-budget-departments) | Null 45 | Lets modders add new budget departments through building exemplars |
| [Custom Ordinance Exemplar Host DLL](/plugin/sc4-custom-ordinance-host) | Null 45 | Lets modders define new ordinances in ordinance exemplars |
| [SC4 Render Services](/plugin/sc4-render-services) | CasperVg | A library DLL with rendering services for other DLL plugins |

## Other DLL Plugins

These DLL plugins do not have their own page yet.

| Plugin | Author | Description |
|----|----|----|
| [Regional Supply/Demand DLL](https://github.com/0xC0000054/sc4-regional-supply-demand) | Null 45 | Adds a basic regional supply and demand system for other mods |
| [Extended Terrain DLL](https://github.com/0xC0000054/sc4-extended-terrain) | Null 45 | Adds support for more terrain types |
| [Legalize Gambling Ordinance Upgrade](https://github.com/0xC0000054/sc4-legalize-gambling-ordinance-upgrade) | Null 45 | Bases the Legalize Gambling ordinance income on the residential population |
| [No Kick Out DLL](https://github.com/0xC0000054/sc4-no-kick-out) | Null 45 | Stops the game from kicking out lower wealth occupants |
| [City Lottery Ordinance DLL](https://github.com/0xC0000054/sc4-city-lottery-ordinance) | Null 45 | Adds a city lottery ordinance to the game |
| [Humane Society Ordinance DLL](https://github.com/0xC0000054/sc4-humane-society-ordinance) | Null 45 | Adds a Humane Society ordinance to the game |
| [Auto Save DLL](https://github.com/0xC0000054/sc4-auto-save) | Null 45 | Saves a city automatically at set intervals |
| [Bulldoze Extensions DLL](https://github.com/0xC0000054/sc4-bulldoze-extensions) | Null 45 | Adds new modes to the bulldoze tool |
| [Region Census DLL](https://github.com/0xC0000054/sc4-region-census) | Null 45 | Adds a region census UI to the region view |
| [SC4 Zoning Extensions](https://github.com/caspervg/sc4-zoning-extensions) | CasperVg | Adds controls for parcel size and roads to the zoning tools |
| [SC4 Terrain Extensions](https://github.com/caspervg/sc4-terrain-extensions) | CasperVg | Adds terrain tools through cheat codes |
| [SC4 Season Jumper](https://github.com/caspervg/sc4-season-jumper) | CasperVg | Runs the simulation to the start of a season, then pauses |
| [SC4 DJEM Fix](https://github.com/caspervg/sc4-djem-fix) | CasperVg | Fixes diagonal jagged edges in steep terrain |
| [SC4 Effects Extensions](https://github.com/caspervg/sc4-effects-extensions) | CasperVg | Tools to author, load and test effects in the game |
| [Discord Rich Presence DLL](https://github.com/0xC0000054/sc4-discord-rich-presence) | Null 45 | Shows game status in Discord rich presence |
| [Disable Demolition Animation DLL](https://github.com/0xC0000054/sc4-disable-demolition-animation) | Null 45 | Disables the demolition animation |
| [Disable Lot Plop Smoke DLL](https://github.com/0xC0000054/sc4-disable-lot-plop-smoke) | Null 45 | Disables the smoke shown after plopping a lot |
| [Disable Network Construction Sounds DLL](https://github.com/0xC0000054/sc4-disable-network-construction-sounds) | Null 45 | Disables the sounds of the network construction animation |

## See Also

- [Plugins](/plugins)
- [Types of Custom Content for SimCity 4](/types-of-custom-content-for-simcity-4)
- [Network Addon Mod](/network-addon-mod)

