---
title: "TRK"
description: ""
published: true
date: '2019-08-09T02:55:03Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T00:17:15Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**TRK** files (Track Definitions) have been known so far simply as sound settings files. They are also referred to as TKD files. These are the files that other things in the game such as UIs, effects, and [exemplars](/exemplar) link to. They contain direct properties for either a single sound or a [Hitlist playlist](/hls), and can link sounds together with a respective [logic object](/tlo). Most of their properties are unknown, however.

The following is a partial specification:

`DWORD  Identifier`  
`DWORD  SoF`  
`Data Block (Comma Separated)`

The **identifier** of a TRK file is always 2DKT. This is always the first 4 bytes in any TRK file so its easy to identify them by. TRK files are never compressed.

**SoF** is the size of the file in bytes after this point. It is a DWORD so it is easy to calculate.

Some TRK files are missing the identifier and SoF fields, and begin with the data block. This is often seen in [Rush Hour](/rush-hour) files.

### Data Block

The **data block** always begins with a **Start Signature**, which is always TKDT in plain text.

The data block is the main settings area of the TRK file. It consists of 30 commas which which separate 31 areas that can hold various types of data. It is unknown exactly what each area represents however.

|          |                 |                 |
|----------|-----------------|-----------------|
| **Item** | **Name**        | **Value**       |
|          | Start Signature | TKDT            |
| 0        |                 | 2               |
| 1        | *unknown*       |                 |
| 2        | XA Instance ID  |                 |
| 3        | TLO Instance ID |                 |
| 4        | *unknown*       | (1 byte)        |
| 5        | *unknown*       | (2 bytes)       |
| 6        | *unknown*       |                 |
| 7        | *unknown*       | (1 byte)        |
| 8        | *unknown*       |                 |
| 9        | *unknown*       | (val)           |
| 10       | *unknown*       | (9 to 10 bytes) |
| 11       | *unknown*       |                 |
| 12       | *unknown*       | (1 byte)        |
| 13       | *unknown*       | (val)           |
| 14       | HLS Instance ID |                 |
| 15       | *unknown*       |                 |
| 16       | *unknown*       |                 |
| 17       | *unknown*       |                 |
| 18       | *unknown*       | (1 byte)        |
| 19       | *unknown*       | (val)           |
| 20       | *unknown*       | (val)           |
| 21       | *unknown*       |                 |
| 22       | *unknown*       |                 |
| 23       | *unknown*       | (5 bytes)       |
| 24       | *unknown*       | (val)           |
| 25       | *unknown*       |                 |
| 26       | *unknown*       |                 |
| 27       | *unknown*       | (1 byte)        |
| 28       | *unknown*       | (1 byte)        |
|          | EoF             | ETKD            |

Val means just any value. Items simply called "val" above are between 1 and 4 bytes long. The 9-10 and 1 byte bits mean that's all that has been seen as its value. This is by no means supposed to be a complete list. Commas with nothing between them means nothing has been seen between them yet. Note that this does not mean data exists and hasn't been deciphered, there is simply *nothing* between the commas.

**EoF** is the end of file signature which is always ETKD immediately after the last comma of the data block.

A Full TRK file might look like this:

2DKTJ...TKDT,2,,0xaa726b1d,0xe9233083,0,32,,1,,50,174302531,,0,1024,0xe9dc0f3e,,,,0,111,1000,,,11111,779,,,0,1,ETKD

While a typical TRK looks like:

2DKTJ...TKDT,2,,,0xe9233083,,,,,,50,,,,1024,0xe9dc0f3e,,,,0,,1000,,,,779,,,0,,ETKD
