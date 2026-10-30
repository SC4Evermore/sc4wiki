---
title: "HLS"
description: ""
published: false
date: '2019-08-09T02:54:55Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T02:15:47Z'
---

**HLS** files are a Hitlist Playlist. Hitlists group [XA](/xa) sounds together and are used in conjunction with [TRK](/trk) definitions and [Logic Objects](/tlo) in the game. Namely, they control the files and the other file types control the variables.

## Format

### Header

     WORD  - major version (1)
     WORD  - minor version (0)
     DWORD - track count

### Repeating Chunk

Repeating chunk, for as many tracks as are in the hitlist:

`DWORD - `[<code>Instance ID</code>](/instance-id)` for an XA or TRK file in the archive.`
