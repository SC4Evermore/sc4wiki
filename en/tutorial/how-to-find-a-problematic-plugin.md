---
title: "How to Find a Problematic Plugin"
description: ""
published: true
date: '2019-08-09T02:32:12Z'
tags: []
editor: markdown
dateCreated: '2009-01-28T07:11:49Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [Diggis](/people/diggis), from [SC4D](/sc4d). [Original tutorial](http://sc4devotion.com/forums/index.php?topic=2401.0).

If you have a problem with your plugins folder, but no idea what it is this is the best way to find it. The first step varies depending on what the problem is so I will break it down a little:

- Step 1:

If you are having crashes empty the plugins folder and run the game to see if it works OK. if so then the problem is something in the plugins.

If you are having a conflict with a plugin remove all of the plugins except the one that the problem is with. Run the game and see if the problem is still there. If so then it's a conflict with something in your plugins folder. If not, it's a problem with the plugin still in there.

- Step 2:

Put back in half your plugins into the folder. (or near enough to half. My BSC folder is approx half anyway so I start with that) Run the game and see if the problem still occurs. If it does then go to step 4a, if not go to step 3.

- Step 3:

Move the folder tested into another location for safe keeping and put the other portion in and run the game to see if the problem still occurs. If so then the issue is with something in this portion of the plugins. Go to step 4a. If not then the issue is most likely a conflict between something in the 2 halves and go to step 4b.

- Step 4a:

With the half that the problem is in still in the game folder begin removing folders from the plugins, checking ingame every time you remove something untill the problem dissapears. The folder last removed contains part of the issue. If it is a conflict with another know file you will need to contact one of the creators to trouble shoot the reason. If it is an issue with 2 unknown files then proceed to step 5.

- Step 4b:

If the problem is a conflict between the two halves then leave one half in there and add in files from the second half until the problem reappears. The file causing the issue is in the last folder added into the plugins folder.

- Step 5:

Using the same process above on the folder contianing the issue work through the levels untill you find the file containing the issue. Leave this file in the plugins and repeat steps 4 and 5 until you find the second file. You now know what files are causing the conflict and have more information to give when asking online about the problem.
