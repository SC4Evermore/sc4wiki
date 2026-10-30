---
title: "TLO"
description: ""
published: true
date: '2019-08-09T02:55:03Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-04T23:57:08Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**TLO** controls logical sound properties and is linked to a sound by its respective [TRK](/trk) file. It is referred to both as TLO and LogicObject, based on internal game data.

## Specification

The structure of the TLO file is a header (8 bytes), followed by repeating chunks (40 bytes each).

### Header

     DWORD - Identifier, always 0.
     DWORD - Number of repeating chunks in file.

### Repeating Chunk

     DWORD - Name Length
        STRING - Effect Name in the EFFDIR files
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD

This format remains unknown, and has not been otherwise figured out. Reference in the MTS2 article to a "S1B Alpha Specification" perhaps as an old name for TLO files.
