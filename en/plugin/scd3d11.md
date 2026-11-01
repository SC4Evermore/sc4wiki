---
title: SCD3D11
description: ''
published: true
date: '2026-11-01T12:06:24.356Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:06:24.356Z'
---

<!-- path: plugin/scd3d11 | title: SCD3D11 | tags: DLL Plugins, Plugins, Customizing the Game -->
<div class="infobox">
<table>
<tr><th colspan="2">SCD3D11</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/caspervg">CasperVg</a></td></tr>
<tr><td><strong>Desc</strong></td><td>A Direct3D 11 renderer that replaces the DirectX 7 renderer of the game</td></tr>
<tr><td><strong>Version</strong></td><td>0.4.7 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/caspervg/scd3d11/releases">GitHub releases</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/caspervg/scd3d11">caspervg/scd3d11</a></td></tr>
</table>
</div>

**SCD3D11** is a DLL plugin for [SimCity 4](/simcity-4) that replaces the DirectX 7 hardware renderer of the game with a Direct3D 11 renderer. It improves compatibility with modern graphics cards, drivers, Windows versions and high-resolution displays. It started as [SCGL](/plugin/scgl), an OpenGL driver by [simmaster07](/people/simmaster07).

## Features

- Renders with current Direct3D 11 drivers instead of DirectX 7.
- Borderless fullscreen, a VSync setting and flip-model presentation.
- Uses the high-performance graphics card on laptops that have two.
- Optional live shadows along the sun of the game.
- [ReShade](https://reshade.me/) effects that leave the user interface unchanged and can use the depth of the city.

The settings are in the file `SCD3D11.ini`. The game selects the driver automatically, so no command line switch is needed. SCD3D11 can be installed together with [SCGL](/plugin/scgl) or [scvk](/plugin/scvk).

## Requirements

- SimCity 4 Deluxe Edition version 1.1.641, on Windows 10 or later.
- A graphics card that supports Direct3D 11.

## See Also

- [SCGL](/plugin/scgl), the OpenGL 3 renderer that SCD3D11 started from
- [scvk](/plugin/scvk), a Vulkan renderer

> **Note:** This article is a stub. You can help by expanding it.

