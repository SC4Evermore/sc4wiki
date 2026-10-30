---
title: "FSH Format"
description: ""
published: false
date: '2019-08-04T05:41:00Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2011-10-12T03:44:22Z'
---

The following is the file format for [FSH](/fsh) files, as developed by [DarkMatter](/people/darkmatter) and [Karybdis](/people/karybdis).

## FSH SHPI Header

The FSH header is 16 bytes in length. The first 4 bytes are always the characters 'SHPI'. This is the file identifier, indicating that it should be a valid FSH. The structure of the header is as follows:

`SHPI  - (4 bytes)`  
`INT32 - File Size`  
`INT32 - Number of Entries `  
`Directory ID - (4 bytes)`

### Directory ID Values

These are valid entries for the Directory ID above.

`G354 - Building Textures`  
`G264 - Network Textures, Sim Textures, Sim heads, Sim animations, Trees, props, Base textures, Misc colors`  
`G266 - 3d Animation textures (e.g. the green rotating diamond in loteditor.dat)`  
`G290 - Dispatch marker textures`  
`G315 - Small Sim texture, Network Transport Model Textures (trains, etc.)`  
`GIMX - UI Editor textures`  
`G344 - BAT gen texture maps`

## FSH Directory

Directly after the 16 byte FSH SHPI Header is the directory. The directory is made up of 8 byte entries, and there should be as many entries as indicated by the third value in the FSH header (# of entries). The structure of an FSH directory entry is as follows:

`Entry Name - (4 bytes)`  
`INT32      - Offset of the entry in the file`

### Entry Names

The entry name sometimes has significance. When searching for a global palette for 8-bit bitmaps, the directory entry name for the gobal palette will always '!pal'. Once the '!pal' directory entry has been found, the global palette can be extracted and used for any bitmaps that use 8-bit indexed color. If no global palette is found, FSH decoders should look for a local palette directly following the indexed bitmap. If no palette is found, then no palette will be created or associated with the bitmap. Most tools, like FSHTool, simply ignore missing palettes and save the bitmap with an empty palette with all indexes set to black.

`!pal - Global palette for 8-bit Indexed Bitmaps.`  
`0000 - Buildings, props, network intersections,and terrain textures.`  
`rail - Always used for a rail texture, whereas for street/road intersections its always by instance.`  
`TB2  - First sprite animation entry in a directory.`  
`TB3  - Any sprite animation entries in a directory after TB2.`

## FSH Entry Header

Each directory entry has an offset, which points to the start of a bitmap or palette. Before the actual palette or bitmap data is an entry header. This header specifies critical information about the data that follows it. The structure of an FSH entry header is as follows:

`BYTE   - Record ID (logically ANDed by 0x7f for bitmap code or 0x80`  
`         to check if the entry is QFS compressed (unused by SC4))`  
`INT24  - Size of the block including this header, only used if the file contains`  
`         an attachment or embedded mipmaps. It is zero otherwise.`  
`         For single images this is usually: width x height + 10h(hex).`  
`         For images with embedded mipmaps, this is the total size of the original image,`  
`         plus all mipmaps, plus the header.`  
`         In either case, it may include additional data as a binary attachment with unknown format.`  
`UINT16 - Width `  
`UINT16 - Height`  
`UINT16 - X axis coordinate for center of image or for image to spin around. 65535 max.`  
`UINT16 - Y axis coordinate for center of image or for image to spin around. 65535 max.`  
`UINT16 - X axis position to display the image from the left.`  
`         Larger values offset image to the right. 4095 max.`  
`         (12 bits, 4 MSB (most significant bits) are always 0).`  
`UINT16 - Y axis position to display the image from the top.`  
`         Larger values offset image down the screen. 4095 max.`  
`         (12 bits, 4 MSB specify number of embedded mipmaps).`

The center coordinates and offsets do not seem to be used by SimCity 4, but the nibble specifying embedded mipmaps is useful.

### Bitmap or Palette Data

After the entry header is the bitmap or palette pixel or color information. Palettes are generally arrays of 1 byte each, 256 entries long. Bitmaps may store their pixel data in one of many ways. FSH images can store their pixel data raw, or they can make use of Microsoft DXTC compressed formats. The following formats and their corresponding codes are as follows:

NOTE: The entry code in the bitmap's entry header is logically ANDed with 0x7F to arrive at the color code (entry.code&0x7F).

#### Bitmap codes

| Code | Type | Palette | Compression |
|----|----|----|----|
| 0x7B | 8-bit indexed | Directly follows bitmap or uses global palette | none |
| 0x7D | 32-bit A8R8G8B8 | none | none |
| 0x7F | 24-bit A0R8G8B8 | none | none |
| 0x7E | 16-bit A1R5G5B5 | none | none |
| 0x78 | 16-bit A0R5G6B5 | none | none |
| 0x6D | 16-bit A4R4G4B4 | none | none |
| 0x61 | DXT3 4x4 packed, 4-bit alpha | none | 4x4 grid compressed, half-byte per pixel |
| 0x60 | DXT1 4x4 packed, 1-bit alpha | none | 4x4 grid compressed, half-byte per pixel |

#### Palette codes

`0x22 - 24-bit DOS`  
`0x24 - 24-bit `  
`0x29 - 16-bit NFS5 `  
`0x2A - 32-bit `  
`0x2D - 16-bit `

#### Text codes

`0x6F - Standard Text file`  
`0x69 - ETXT of arbitrary length with full entry header `  
`0x70 - ETXT of 16 bytes or less including the header `  
`0x7C - defined Pixel region Hotspot data for image.`

The Bitmap or Palette Data entry can also contain Binary data, however the identifier byte for different binary types anything that isn't already defined with a type so make sure to try and get all codes down correctly. Examples of binary data consist of Palette animations, binary links to outside files, or plain binary data.

Bitmaps can contain embedded mipmaps (pre-generated reduced size images). Each successive mipmap is assumed to be exactly 1/4 the size of the last (1/2 width and 1/2 height). The dimensions of the original bitmap must be a multiple of 2 raised to the power of the number of mipmaps (eg: 2 ^ 1 for one mipmap, 2 ^ 4 or 16 for four mipmaps).

Each mipmap is encoded using the same scheme as the original image and its data block is appended directly following the previous mipmap or original image in descending order. (Exception: DXT encoded bitmaps must be at least 4x4 pixels, but a 2x2 pixel mipmap is supported under this scheme. Its format is unknown.)

## Overview of DXT Compression

Microsoft's DirectX Texture Compression uses what they call a 4x4 encoding. Basically, an image must be a multiple of 4 in width and height, because 4x4 blocks of pixels are compressed at a time, similar to encoding used in AVI/MPEG files. Each 4x4 block contains 16 pixels, each pixel using either 24bits or 32bits before compression. All 16 pixels use 512 bits of storage before compression. After compression, that block of 16 pixels is reduced to 64 bits, for an 8:1 compression ratio. The nice thing about DXT compression is that it is hardware accelerated by nVidia and ATI GPU's all the way back to the GeForce2 and Raedon 8000 series, leaving the CPU free to simulate.

The compression itself works in the following way. First, all 16 pixels in the 4x4 block are checked, and unique colors stored in a vector (usually just an array of 16 unsigned ints). Once all the pixels in a block are checked, the two color extremes are found among all the unique colors. (Currently just using the method from FSHTool.) These two color extremes make up color1 and color2.

Once color1 and color2 are found, they are reduced from 32bit color to 16bit color (RGB 5:6:5), and stored in the first 32bits of the compressed 64bit chunk of data. The rest of the colors in the 4x4 block are interpolated between thse two colors. Each pixel is only represented by two bits of information, as follows:

`Bits    Color used for pixel`  
`---------------------------------`  
`00      color1`  
`01      color2`  
`10      2/3 color1 + 1/3 color2`  
`11      1/3 color1 + 2/3 color2`

Here is the layout of a 64bit compressed block:

`|----------------------------|`  
`| 16bit RGB (5:6:5) color1   | <- 2 bytes`  
`|----------------------------|`  
`| 16bit RGB (5:6:5) color2   | <- 2 bytes`  
`|----------------------------| `  
`|  00  |  01  |  01  | 11    | <- 1 byte, first 4 pixels`  
`|----------------------------| `  
`|  01  |  11  |  00  | 11    | <- 1 byte, second 4 pixels`  
`|----------------------------| `  
`|  00  |  01  |  01  | 01    | <- 1 byte, third 4 pixels`  
`|----------------------------|`  
`|  11  |  11  |  00  | 00    | <- 1 byte, fourth 4 pixels`  
`|----------------------------|`

You can see the second part of the block is very basic. It's a simple bitmap of 2 bits each representing 1 of four possible color values, following the definitions above. This is DXT1 compression, as no alpha information is saved. DXT3 compression uses the same technique, but also stores another 64bits of information for the alpha component of each pixel, in a similar block. So DXT3 compression achieves a 4:1 compression ratio with alpha information included, rather than the 8:1 compression ratio without.
