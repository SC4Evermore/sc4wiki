---
title: SCGL
description: ''
published: true
date: '2026-11-01T12:12:38.068Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:12:38.068Z'
---

<!-- path: plugin/scgl | title: SCGL | tags: DLL Plugins, Plugins, Customizing the Game -->
<div class="infobox">
<table>
<tr><th colspan="2">SCGL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/simmaster07">simmaster07</a></td></tr>
<tr><td><strong>Desc</strong></td><td>An OpenGL 3 renderer for the game</td></tr>
<tr><td><strong>Version</strong></td><td>1.0.0 (February 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/nsgomez/scgl/releases">GitHub releases</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/nsgomez/scgl">nsgomez/scgl</a></td></tr>
</table>
</div>

**SCGL** (pronounced _sigil_) is a DLL plugin for [SimCity 4](/simcity-4) that replaces the game's OpenGL hardware rendering engine. It is an OpenGL 3 renderer. Its goal is to fix problems with modern graphics drivers and Windows versions. [SCD3D11](/plugin/scd3d11), a Direct3D 11 renderer, is based on SCGL.

## Features

- Replaces the original OpenGL renderer with one that targets OpenGL 3.0.
- Addresses performance problems of the original OpenGL driver.
- Version 1.0.0 mostly works on Windows. It has known issues with alpha blending on shadows and automata.
- You turn it on with the `-d:OpenGL` startup option.

## Requirements

- Windows Vista or later.
- A graphics card that supports OpenGL 3.0, such as a GeForce 8000 (2006) or equivalent.
- It cannot be installed together with [scvk](/plugin/scvk), because both use the same class ID. It can be installed together with [SCD3D11](/plugin/scd3d11).

## See Also

- [SCD3D11](/plugin/scd3d11), a Direct3D 11 renderer based on SCGL
- [scvk](/plugin/scvk), a Vulkan renderer

> **Note:** This article is a stub. You can help by expanding it.

