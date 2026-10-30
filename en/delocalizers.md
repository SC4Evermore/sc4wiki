---
title: "Delocalizers"
description: ""
published: true
date: '2019-08-04T05:40:34Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T01:17:30Z'
---

The **Delocalizer** file tells the game what characters it can and can't localize to the player's language. It is important that this is included with plugins and in *SimCityLocale.dat* due to those files containing [LTEXTs](/ltext) which are unicode and are applied to this. The [TGI](/tgi) for the Delocalizer is *2026960b 6a231eaa 0a6df4df*, which places it as an LTEXT file itself, however it cannot be read as a plain text file like an LTEXT can.

## Specification

The format of the Delocalizer is:

     DWORD    - Size of file minus this Dword
     16 Bytes - "Don't localize. " In plain Text
     BYTE     - x - Marks the beginning of the string
     Unicode for non-localizable text characters
     BYTE     - x - Marks the end of the string
