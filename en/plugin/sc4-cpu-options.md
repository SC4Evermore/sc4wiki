---
title: CPU Options DLL
description: ''
published: true
date: '2026-11-01T11:57:31.563Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T11:57:31.563Z'
---

<!-- path: plugin/sc4-cpu-options | title: CPU Options DLL | tags: DLL Plugins, Plugins, Bugs, Customizing the Game -->
<div class="infobox">
<table>
<tr><th colspan="2">CPU Options DLL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/null-45">Null 45</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Sets the CPU core use and priority of the game</td></tr>
<tr><td><strong>Version</strong></td><td>1.1.0 (October 2026)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/0xC0000054/sc4-cpu-options/releases">GitHub releases</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/0xC0000054/sc4-cpu-options">0xC0000054/sc4-cpu-options</a></td></tr>
</table>
</div>

The **CPU Options DLL** is a DLL plugin for [SimCity 4](/simcity-4) that configures the CPU core count and priority of the game. It has no settings: everything is automatic. It replaces the [Single CPU DLL](https://github.com/0xC0000054/sc4-single-cpu) and the [CPU Priority DLL](https://github.com/0xC0000054/sc4-cpu-priority). Remove those two plugins when you install it.

## Features

- Runs the game's own threads on one core. This avoids the game's multi-core crashes.
- Runs the game at high CPU priority. A `-CPUPriority` command line argument still overrides this.
- Keeps the game on the performance cores of hybrid Intel CPUs. Windows 11 no longer slows the game down when it is in the background.
- Shares the search for visible objects in the 3D view among other cores (parallel render cull).

Command line arguments can turn parts off. The plugin overrides the CPU priority that third-party launchers set.

## Requirements

- Windows 10 or later.
- The parallel render cull and the simulation limit need SimCity 4 version 1.1.641. On other versions they stay off.

> **Note:** This article is a stub. You can help by expanding it.

