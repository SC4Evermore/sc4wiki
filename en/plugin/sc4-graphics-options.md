---
title: Graphics Options DLL
description: ''
published: true
date: '2026-11-01T12:02:52.711Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:02:52.711Z'
---

<!-- path: plugin/sc4-graphics-options | title: Graphics Options DLL | tags: DLL Plugins, Plugins, Customizing the Game -->
<div class="infobox">
<table>
<tr><th colspan="2">Graphics Options DLL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/null-45">Null 45</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Sets the game's rendering mode and resolution options</td></tr>
<tr><td><strong>Version</strong></td><td>1.4.1 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/0xC0000054/sc4-graphics-options/releases">GitHub releases</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/0xC0000054/sc4-graphics-options">0xC0000054/sc4-graphics-options</a></td></tr>
</table>
</div>

The **Graphics Options DLL** is a DLL plugin for [SimCity 4](/simcity-4) that sets the game's rendering mode and resolution options. The options are set in an INI file, so no command line arguments or launcher are needed.

## Features

- Sets a custom resolution, color depth and window mode, including borderless full screen.
- Changes the rendering driver: DirectX, OpenGL, [SCGL](/plugin/scgl) or Software.
- Lets full screen mode use 32-bit color.
- Can turn off the intro video and pause the game when it loses focus.
- Has a "force draw on scroll" option for graphics cards that show screen tearing.

## Requirements

- SimCity 4 version 1.1.641 for the full screen 32-bit color fix. The other features should work on older game versions.
- Windows 10 or later. It may work on Windows 7 or later with the Microsoft Visual C++ 2022 x86 Redistributable, but this is untested.
- A DirectX wrapper, such as dgVoodoo 2 or DxWrapper, or [SCD3D11](/plugin/scd3d11) for resolutions above 2048x2048 with the DirectX driver.

> **Note:** This article is a stub. You can help by expanding it.

