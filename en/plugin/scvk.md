---
title: scvk
description: ''
published: true
date: '2026-11-01T12:07:09.537Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:07:09.537Z'
---

<!-- path: plugin/scvk | title: scvk | tags: DLL Plugins, Plugins, Customizing the Game -->
<div class="infobox">
<table>
<tr><th colspan="2">scvk</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td>aspctt</td></tr>
<tr><td><strong>Desc</strong></td><td>A Vulkan renderer for the game</td></tr>
<tr><td><strong>Version</strong></td><td>0.4.0 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/aspctt/scvk/releases">GitHub releases</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/aspctt/scvk">aspctt/scvk</a></td></tr>
</table>
</div>

**scvk** is a DLL plugin for [SimCity 4](/simcity-4) that replaces the game's renderer with one built on Vulkan. The author describes it as stable. The whole game draws with it, from the region view to cities and menus.

## Features

- Runs faster than the game's DirectX 7 renderer in all benchmark scenes, most of all when zoomed out.
- Starts the game borderless by default. Launch options give windowed or fullscreen mode instead.
- Raises the frame rate limits up to the display's refresh rate, so [Disable FPS Limits](/plugin/sc4-disable-fps-limits) is not needed.
- Has optional live True3D shadows, which are off by default.
- Works with [SC4Fix](/plugin/sc4fix) and the [Graphics Options DLL](/plugin/sc4-graphics-options).

## Requirements

- SimCity 4 version 641, on Windows 10 or 11, or Linux through Wine or Proton.
- A graphics card with Vulkan support.
- It cannot be installed together with [SCGL](/plugin/scgl), because both use the same class ID. It can be installed together with [SCD3D11](/plugin/scd3d11).
- [SC4 Render Services](/plugin/sc4-render-services) users need version 0.8.3 or later.

The DLL is also available in [sc4pac](https://memo33.github.io/sc4pac/channel/?pkg=aspct:scvk) as `aspct:scvk`.

## See Also

- [SCGL](/plugin/scgl), an OpenGL 3 renderer
- [SCD3D11](/plugin/scd3d11), a Direct3D 11 renderer

> **Note:** This article is a stub. You can help by expanding it.

