---
title: "KEYCFG/TAB"
description: ""
published: false
date: '2019-08-09T02:54:56Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-09-07T23:40:17Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

The **TAB** or **KEYCFG** files define keyboard shortcuts for [SimCity 4](/simcity-4). They are made up of tables of entries following the format below. Most of the default shortcut definitions have only the KeyCombination, MsgID, and Description. See TGI 0xa2e3d533, 0x6a231eaa, 0x6a9362ef (City View keyboard shortcuts) for more information.

## Entry format

<KeyCombination>` = `<MsgID>` [[[`<data1>`] `<data2>`] `<data3>`] [`<Description>`]`

Example:

`Control M = 0xec3e82f8 0x8bd88057 "Build Passenger Ferry Terminal"`

KeyCombination is any combination of the keys that you want to use to activate this function.

MsgID is the coded ID in the game's .exe that activates this command. It may call an in-game message code. Adding a new key combination requires knowing the MsgID for that command.

data1,2,3 are specific data IDs (which are usually [Exemplars](/exemplar)) that are used in conjunction with this action. The above example has the data1 as the exemplar for the ferries.

Description is a simple description of the function of the key combination.
