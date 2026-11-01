---
title: Resource Loading Hooks DLL
description: ''
published: true
date: '2026-11-01T11:54:50.622Z'
tags: []
editor: markdown
dateCreated: '2026-11-01T11:54:50.622Z'
---

<!-- path: plugin/sc4-resource-loading-hooks | title: Resource Loading Hooks DLL | tags: DLL Plugins, Plugins, Modding -->
<div class="infobox">
<table>
<tr><th colspan="2">Resource Loading Hooks DLL</th></tr>
<tr><td><strong>Type</strong></td><td>DLL Plugin</td></tr>
<tr><td><strong>Author</strong></td><td><a href="/people/null-45">Null 45</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Allows DLLs to modify resources as the game loads them</td></tr>
<tr><td><strong>Version</strong></td><td>2.0.1 (September 2025)</td></tr>
<tr><td><strong>Downloads</strong></td><td><a href="https://github.com/0xC0000054/sc4-resource-loading-hooks/releases">GitHub releases</a><br><a href="https://community.simtropolis.com/files/file/36242-resource-loading-hooks-dll-for-simcity-4/">Simtropolis</a></td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/0xC0000054/sc4-resource-loading-hooks">0xC0000054/sc4-resource-loading-hooks</a></td></tr>
</table>
</div>

The **Resource Loading Hooks DLL** is a DLL plugin for [SimCity 4](/simcity-4) that allows other DLLs to modify resources as the game loads them. It also adds exemplar patching. Many other plugins need it, such as the [Submenus DLL](/plugin/submenus-dll).

## Features

- Adds exemplar patching. An exemplar patch is a Cohort file that adds or changes properties in other exemplars when the game loads them. The original DBPF files are not changed.
- One exemplar patch can target several exemplars, and several patches can target the same exemplar.
- Gives other DLLs interfaces to modify exemplars as they load, and to log exemplar load errors.
- Adds the `-exemplar-log:` and `-exemplar-patch-debug-logging` command line arguments for logging.

## Requirements

- SimCity 4 version 641.
- Windows 10 or later. It may work on Windows 7 or later with the Microsoft Visual C++ 2022 x86 Redistributable, but this is untested.

> **Note:** This article is a stub. You can help by expanding it.

