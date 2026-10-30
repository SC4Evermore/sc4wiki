---
title: "Plugin Loading Order"
description: ""
published: false
date: '2019-08-09T09:35:15Z'
tags: ["The Game", "Custom Content", "Customizing the Game"]
editor: markdown
dateCreated: '2009-01-13T08:16:07Z'
---

The game loads [plugins](/plugins) in a particular way

## Install Location

This is where all the main program files are held, including the EXE and the simcity\_\*.dat files

The default location is

    C:\Program Files\Maxis\SimCity 4\

and can be symbolised as

    %InstallDir%\

## Documents Location

This is where the users information is held. it is usually found in

    My Documents\SimCity 4\

but can be moved using the [-userdir](/tutorial/shortcut-parameters) shortcut parameter and will be symbolised throughout as

    %LocalDir%

## Order

In any single directory it will load loose files first, then subdirectories, and then .dat files. The order algorithm is just an alphabetic sort, with non-alphanumericals at the end.

First it loads the files in %InstallDir%\\

Then it loads %InstallDir%\Plugins\\

Then %LocalDir%\Plugins\\

(but what about maps and the other folders)

> **Note:** This article needs expanding.
