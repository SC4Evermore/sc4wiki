---
title: Lua Sandbox DLL
description: ''
published: true
date: '2026-11-01T12:18:00.142Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T12:18:00.142Z'
---

<!-- path: plugin/sc4-lua-sandbox-dll | title: Lua Sandbox DLL | tags: DLL Plugins, Plugins, Modding -->
<div class="infobox">
<table>
<tr><th colspan="2">Lua Sandbox DLL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/memo">memo</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Blocks unsafe Lua functions that mods could use</td></tr>
<tr><td><strong>Version</strong></td><td>1.0.0 (March 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/memo33/sc4-lua-sandbox-dll/releases">GitHub releases</a><br><a href="https://community.simtropolis.com/files/file/37389-lua-sandbox-dll/">Simtropolis</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/memo33/sc4-lua-sandbox-dll">memo33/sc4-lua-sandbox-dll</a></td></tr>
</table>
</div>

The **Lua Sandbox DLL** is a DLL plugin for [SimCity 4](/simcity-4) that stops mods from using unsafe Lua functions. The game uses Lua scripts for advisor messages, rewards and automata generators. Plugins generally have no need to access the file system, so the DLL blocks this.

## Features

- Blocks unsafe Lua functions, such as reading and writing files and running shell commands.
- Writes a log file that shows if a plugin tried to call a blocked function.
- An optional INI file can allow file reading, while still blocking file writing.
- Works with nearly all plugins. It is not compatible with DAMN, BSC Regional Tracking and Cori Reports.

## Requirements

- SimCity 4 version 1.1.641 (the digital release), on Windows 10 or later, or Linux.
- The Microsoft Visual C++ 2022 or later x86 Redistributable.

The DLL is also available in [sc4pac](https://memo33.github.io/sc4pac/channel/?pkg=memo:lua-sandbox-dll) as `memo:lua-sandbox-dll`.

> **Note:** This article is a stub. You can help by expanding it.

