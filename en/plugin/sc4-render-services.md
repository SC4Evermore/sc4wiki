---
title: SC4 Render Services
description: ''
published: true
date: '2026-11-01T12:12:13.593Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:12:13.593Z'
---

<!-- path: plugin/sc4-render-services | title: SC4 Render Services | tags: DLL Plugins, Plugins, Modding, User Interface -->
<div class="infobox">
<table>
<tr><th colspan="2">SC4 Render Services</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/caspervg">CasperVg</a></td></tr>
<tr><td><strong>Desc</strong></td><td>A library DLL with rendering services for other DLL plugins</td></tr>
<tr><td><strong>Version</strong></td><td>0.8.3 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/caspervg/sc4-render-services/releases">GitHub releases</a><br><a href="https://community.simtropolis.com/files/file/37423-sc4renderservices-dll/">Simtropolis</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/caspervg/sc4-render-services">caspervg/sc4-render-services</a></td></tr>
</table>
</div>

The **SC4 Render Services** is a DLL plugin for [SimCity 4](/simcity-4) that gives rendering services to other DLL plugins. It adds nothing in the game by itself. You install it when another plugin needs it, such as [SC4 Plop and Paint](/plugin/sc4-plop-and-paint) and [SC4 Terrain Extensions](/plugin/sc4-terrain-extensions)

## Features

- Gives plugins ImGui panels, so they can show their own windows in the game.
- Lets plugins draw shapes, lines and textures into the city.
- Has services for the camera, draw pass callbacks and terrain decals.
- Works with the game's built-in DirectX driver, Software rendering, [SCD3D11](/plugin/scd3d11) and [scvk](/plugin/scvk).

## Requirements

- SimCity 4 version 1.1.641.

> **Note:** This article is a stub. You can help by expanding it.

