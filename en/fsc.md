---
title: "FSC"
description: ""
published: true
date: '2019-08-09T02:54:54Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T02:07:07Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**FSC** files are sound playback (Freshness Score) levels files, originally developed for [SimCity 3000](http://en.wikipedia.org/wiki/SimCity_3000). They are also known as, and listed in [Reader](/reader) as **LEV** files. Note, however, that not everything listed in Reader as a LEV file is actually one, some are [XA](/xa) files, and vice versa. In general, FSC/LEV files are in the range of 300-700 bytes and compressed.

### Format

FSC/LEV files consist of global data, and repeating entries for individual sounds, in the following format.

`version 7 (in plain text)`  
`Global Headers`  
`Global Values`  
`Individual Entry Headers`  
`Individual Entry Values`

### Headers

The headers for the **Global Block** are:

`#     - Begin Global Block`  
`vol   - Global Volume for the Files group`  
`pri   - Sound Priority`  
`min   - Optimum Min Tracks to play at a time (target #)`  
`max   - Optimum Max Tracks to play at a time (target #)`  
`rows  - Usable Active Lev Rows (seems to control if all lines in a LEV can be used)`  
`cols  - Usable Active Lev Cols (doesn't seem to work)`  
`tempo - Tempo to play these sounds at`  
`BPB   - Beats per bar (determines frame reference for sound)`  
`SelX  - Selective Processing (how far sound is heard) (Horizontal)`  
`SelY  - Selective Processing (how far sound is heard) (Vertical)`  
`QuanX - Quantization Modifier (Horizontal)`  
`QuanY - Quantization Modifier (Vertical)`  
`DifX  - Diffusion Modifier (Horizontal)`  
`DifY  - Diffusion Modifier (Vertical)`

The headers for the **Individual Entry Block** are:

`#     - Begin Entry Block`  
`vol   - Volume for this sound`  
`rand? - random volume? - bool 1/0`  
`LR    - split amount for left right channels out of 1024`  
`FB    - front and back channels split of 1024 (standard for both LR and FB is 512`  
`rand? - random left right front and back channel splitting? bool 1/0`  
`fin   - fade in time in ms`  
`fout  - fade out time in ms`  
`dly   - Starting delay in ms`  
`rand? - random starting delay? bool 1/0`  
`loop  - Number of times to loop the sound`  
`loop? - Loop sound infinitely`  
`quant - Audio Quantization Value`  
`prob  - Playing probability of this sound as opposed to others in the file.`  
`pitchL - Low Pitch sound modifier (value to modify low pitch sound by)`  
`pitchH - High Pitch Sound modifier (value to modify high pitch sound by)`  
`fast?  - Do fast play of sound? bool 1/0`  
`groupID - Control Group ID`  
`stereo? - play sound in stereo? bool 1/0`  
`filename - The true filename for this sound (lost with dat but still has IID)`  
`exclusion cells - Sound Exclusion Cell Coordinates. Format : (x,z) (x,z) etc`

Normally blank rows are left between either groups of sounds inside a levels file or at the end of the file to mark out various grouping types. Properties are in a table format under a line for their respective block header and column text labels.

Levels are linked to their respective XA files by [Group ID](/group-id). Before compilation of the SC4 engine, files were linked via file names inside the levels file.
