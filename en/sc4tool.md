---
title: "SC4Tool"
description: ""
published: true
date: '2019-08-09T02:36:21Z'
tags: ["Tool", "Custom Tools"]
editor: markdown
dateCreated: '2008-08-31T20:46:38Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">SC4Tool</th></tr>
<tr><td><strong>Downloads</strong></td><td>Somewhere</td></tr>
<tr><td><strong>Desc</strong></td><td>A modding program that helps in doing more complex tasks like <a href="/te">transit enabling</a> and others.</td></tr>
</table>
</div>

SC4Tool features a collection of useful tools both for [BAT](/bat) and lot developers and [SimCity 4](/simcity-4) players. It was started by [Andreas](/people/andreas) as a database for all [Maxis](/maxis) growables, and since then grew to its current shape. The programming was done by [simrolle](/people/simrolle).

## Features

### SimCity 4 Building Database

A database of all 553 RCI buildings by Maxis, featuring building names, tile set, growth stage, pollution values and much more. For each building, an in-game screenshot is included (the screenshots are provided in a separate download). You can use this module for informational and educational purposes. This is esp. usefully for developers who want to assign reasonable values to their BATs and lots, since the values the Plugin Manager suggests are often way off from the values the original Maxis buildings have.

### SimCity 4 Building Reference

Similar to the building database, this module provides information for all in-game civic buildings, such as police stations, schools, power plants etc. Screenshots are not included yet.

### Analyser/Importer

Use this tool to read any information from your custom BATs and lots, including textures and dependencies. The Analyser also features a HTML ReadMe export that can use custom HTML templates. Placeholders can be used for any values, which are automatically replaced by the actual values of the lot. You can also include screenshots of your work and add a custom description, as well as selecting names of BAT teams and authors.

### Texture Scanner

This module is used automatically by the Analyser for searching texture pack dependencies. You can also use it as a stand-alone tool for managing and evaluating the installed textures/texture packs.

### Dependencies Scanner

The dependencies scanner is used by the Analyser as well to detect prop and texture packs. You can also use it as a standalone tool for detecting the dependencies of all files that are installed, or to check specific files or folders. Missing IDs can be written in a report, so you might be able to find the matching dependencies (i. e. with the help of the BSC [Texture Index](/texture-index)).

### Texture Creator

Open existing texture DATs and add/modify textures or create new DATs. Supports base, overlay and network textures.

### Transit Enabling Editor

This editor allows you to make lots transit enabled via drag & drop. Even complicated transit enabling tasks can be performed in minutes by selecting the necessary values in easy-to-understand dialogue boxes.

### Comparer

The Comparer was designed to compare several BATs and lots directly with each other, in order to detect values that exceed the usual range (future versions of SC4Tool will have referene values in the yellow line in the upper part of the window). With this tool, it's easy to spot buildings that are producing too much garbage or other values that are off. You can also edit the values and save the lots individually or together afterwards.

### Exemplar Editor

The Exemplar Editor allows you to edit values in building and lot exemplar files, similar to the Comparer. But with this tool, all properties are displayed in an easy-to-use tree view, and there's also a small information line where every property and the range of possible values are displayed.

### FileMerger

The FileMerger can be used to merge separate files to a single DAT file, i. e. for creating prop and texture files. Unlike similar tools, you can also merge whole folder trees in one step, and the FileMerger is capable of checking for doubled files and other inconsistencies. If you want, you can also remove all files that are not necessary for the game, this will keep the filesize of the DATs as small as possible.

### Language Editor

Use this tool to translate all captions to your own language. English, German, Dutch, Finnish, Portuguese and Spanish language files are already included. Please send us your custom language file, so we can include it into later versions of the program.

### Property Editor

This tool is mainly a reference list for all properties, including a search function, and you can also edit all information text lines (i. e. for translation). It's also possible to add new properties, such as user-defined occupant groups.

## System Requirements

- Windows 98 or above
- Microsoft .NET Framework 1.1

## Known bugs

The most common bug is caused by an unfortunate combination of issues that prevent the Mac version of SimCity to display the Transit Switch Capacity value properly in the game. This can be fixed by setting the REP count to 0 (instead of 1) with another modding program, such as ilive's Reader. SC4Tool is known to have certain issues on a Windows Vista machine, which can be fixed by disabling visual styles for the program. However, a few issues regarding the texture creator remain.

### Vista and Textures

The SC4Tool uses a dll, called FSHlib, Vista and this dll have some problems, so any tool that uses it won't work properly when using FSH files. Thankfully a fix was made by to solve this, and you can download a vista compatible dll in [this thread at SC4D](http://sc4devotion.com/forums/index.php?topic=5142.msg221467#msg221467)
