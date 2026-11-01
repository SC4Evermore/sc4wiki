---
title: Lua Extensions DLL
description: ''
published: true
date: '2026-11-01T12:09:08.082Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:09:08.082Z'
---

<!-- path: plugin/sc4-lua-extensions | title: Lua Extensions DLL | tags: DLL Plugins, Plugins, Modding -->
<div class="infobox">
<table>
<tr><th colspan="2">Lua Extensions DLL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/null-45">Null 45</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Adds new functions for the game's Lua scripts</td></tr>
<tr><td><strong>Version</strong></td><td>1.5.1 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/0xC0000054/sc4-lua-extensions/releases">GitHub releases</a><br><a href="https://community.simtropolis.com/files/file/36925-lua-extensions-dll/">Simtropolis</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/0xC0000054/sc4-lua-extensions">0xC0000054/sc4-lua-extensions</a></td></tr>
</table>
</div>

The **Lua Extensions DLL** is a DLL plugin for [SimCity 4](/simcity-4) that adds new functions for the game's Lua scripts. It is mainly for modders who write Lua scripts.

## Features

- Adds a number of new functions that Lua scripts can use.
- Turns the Lua error logging back on. Maxis turned it off in the retail game.
- Adds the region view cheat codes `ShowMaxisLuaDebugText` and `HideMaxisLuaDebugText`. They control whether the Maxis Lua debug text goes into the log.
- Blocks the Lua commands that give access to the Windows Registry (since version 1.5.1).
- Lets other DLLs get a callback when the game loads package scripts.

## Requirements

- SimCity 4 version 641.
- Windows 10 or later, with the Microsoft Visual C++ 2022 x86 Redistributable. It may work on Windows 7 or later, but this is untested.

> **Note:** This article is a stub. You can help by expanding it.

