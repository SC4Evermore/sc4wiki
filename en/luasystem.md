---
title: "LUASystem"
description: ""
published: true
date: '2019-08-04T05:40:52Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-15T21:19:23Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**[LUA](/lua) System**, or General files, are composed of blocks of any of the following:

- An opening block with dofile(" ") commands.
- A function.
- A command or a definition, like (*etcetera=game.constants_etcetera* or *return 0*).
- A definition block (see [LUADefs](/luadefs)).
- An *if* statement (IF variable is true, do this, etc.)
- An ending block consisting of more *if* statements or verifying statements.

These will all adhere to the various definitions scripts in the game as well as LUA standards.

Each DAT file can contain its own LUA (any instance number) and will auto-execute based on the top of the LUA file containing the following package signature:

    --#-package:BD008913#

The package number must also be unique, for which you can use the generated [Instance ID](/instance-id). However, if you have two dat files with LUA's with the same package number, one will not work, depending on the load order. If the LUA file does not execute, try changing the first character of the Package ID to "0". During a test, it was found that the generated ID of *:A3506332* was not valid. However *:03506332* was valid. The reason for this is not understood.

Some or all of this information was contributed by [Ralph](/people/ralph)
