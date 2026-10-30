---
title: "MXF"
description: ""
published: false
date: '2022-11-27T05:38:09Z'
tags: ["Customizing the Game", "Modding", "File Formats/SC4"]
editor: markdown
dateCreated: '2022-11-27T05:38:09Z'
---

**Maxis Font (MXF)** is a proprietary wrapper format for standard fonts used in SimCity 4. It is trivial to convert between PostScript Type 1 Binary (.pfb) or TrueType (.ttf) files and Maxis Font files.

## Format

This is the header of MXF Files:

**`CHAR[4]`**  
` Magic Identifier. Always "MXFN"`  
**`DWORD`**  
` Unknown Bytes. Always "02 62 5A 00" in SimCity 4`  
**`BYTE`**  
` Mask Byte. Always 0x9D in SimCity 4`  

Following this, the remainder of the data is an enciphered font blob, padded out to the next multiple of (decimal) 10000 bytes with random data. This isn't checked by the game, and is apparently only an anti-reverse enginering feature, so modded fonts can leave this padding off.

The enciphered font blob is a standard font (PFB or TTF) that has been xor'd with the mask byte.

## Python Encoding Script

Here is a python 3.8+ script to convert TTF or PFB files to MXF files:

    import sys

    mask=0x9D
    prefix=b'MXFN\x02bZ\0'
    if len(sys.argv)!=3:
        print("Usage: python3 encode.py input.{ttf,pfb} output.mxf")
    else:
        with open(sys.argv[1],"rb") as ttf:
            with open(sys.argv[2],"wb") as out:
                out.write(prefix)
                out.write(mask.to_bytes(1, sys.byteorder))
                while (byte:=ttf.read(1)):
                    out.write((int.from_bytes(byte,sys.byteorder)^mask).to_bytes(1, sys.byteorder))
                # we could pad to 10,000 bytes, as Maxis fonts do, but it is not necessary for modding

**Modding note**: You must edit the [Font Table](/font-table) [INI](/ini) files, or ensure your font has as compatible PS name embedded in it. Simply replacing fonts under fonts\\ isn't enough, the internal names must match.
