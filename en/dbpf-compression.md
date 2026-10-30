---
title: "DBPF Compression"
description: ""
published: true
date: '2019-08-04T05:40:55Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2009-11-27T18:20:22Z'
---

## Overview

As noted in the article on the [DBPF](/dbpf) file type, some of the files within DBPF files may be compressed. The idea behind the compression is to reuse previously decoded strings. For example, if the word "heureka" occurs twice in a file, the second occurrence would be encoded by pointing to the first, thus lowering the size of the file.

The compression is done by defining control characters that tell three things:

1.  How many characters of plain text that follow should be appended to the output.
2.  How many characters should be read from the already decoded text (and appended to the output).
3.  Where to read the characters from in the already decoded text.

Thus, the algorithm to decompress these files goes like this:

Read the first 4 bytes, this is the size of the following header + compressed data. (Only if the QFS compressed data is in an older DBPF file, in SimCity 2013 and possibly other games like Spore these redundant 4 bytes are not here).

Read the 5 byte header, which is formatted like so:

`Offset 00 - Compression ID (0x10FB) (QFS Compression)`  
`Offset 02 - Uncompressed Size of file`

Offset 05 is the start of the actual compressed file data, which is handled like so:

`{ `  
`   - Read the next control character. `  
`   - Depending on the control character, read 0-3 more bytes that are a part of the control character.`  
`   - Inspect the control character.  From this, find out `*`how many`*` characters should be read and `*`where from`*`.`  
`   - Read 0-`*`n`*` characters from source and append them to the output.`  
`         (`*`n`*` being the "how many" data from above)`  
`   - Copy 0-`*`n`*` characters from somewhere in the output to the end of the output.`  
`         (`*`n`*` in this case is the "where from" from above)`  
`}`

## Control Characters

There are 4 types of control characters. These are used with different restrictions on how many characters that can be read and from how far behind these can be read. The following conventions are used to describe them:

CC length  
Length of control character.

Num plain text  
Number of characters immediately after the control character that should be read and appended to output.

Num to copy  
Number of chars that should be copied from somewhere in the already decoded output and added to the end of the output.

Copy offset  
Where to start reading characters when copying from somewhere in the already decoded output.

This is given as an offset from the current end of the output buffer, i.e. an offset of 0 means that you should copy the last character in the output and append it to the output. And offset of 1 means that you should copy the second-to-last character.

byte0  
first byte of control character.

Bits  
Bits of the control character.

- p - num plain text
- c - num to copy
- o - copy offset
- i - identifier.

Notes: when the bits are spread over multiple bytes, the bits should be concatenated rather than simply added (hence the bit shifts when the bits are already at the low end of the byte). So in the 0x00-7F CC: 0**oo**cccpp oooooooo, the offset will be **oo**oooooooo (10 bits long), rather than **oo** + oooooooo (8 bits long).

Note: It can sometimes be confusing when a control character states that you should copy, for example, 10 characters 5 steps from the end of the output. Clearly, you cannot read more than 5 characters before you reach the end of the buffer. The solution is to read and write one character at the time. Each time you read a character you copy it to the end thereby increasing the size of the output. By doing this, even offset 0 is possible and would result in duplicating the last character a number of times. This is utilized by the compression to recreate repeating text, for example bars of repeating dashes.

This is the simplest form of control character. The only thing it does is tell how many plain text characters follow. The formula for this is: (C - 0x7F) \* 4. Thus a value of 0xE0 means that you should read 4 characters of plain text and append to the output.

### 0x00 - 0x7F

`CC length:      2 bytes`  
`Num plain text: byte0 & 0x03`  
`Num to copy:    ( (byte0 & 0x1C) > > 2) + 3`  
`Copy offset:    ( (byte0 & 0x60) < < 3) + byte1 + 1`

`Bits: 0oocccpp oooooooo`  
`Num plain text limit: 0-3`  
`Num to copy limit:    3-10`  
`Maximum Offset:       1024`

### 0x80 - 0xBF

`CC length:      3 bytes`  
`Num plain text: ((byte1 & 0xC0) > > 6 ) & 0x03`  
`Num to copy:    (byte0 & 0x3F) + 4`  
`Copy offset:    ( (byte1 & 0x3F) < < 8 ) + byte2 + 1`

`Bits: 10cccccc ppoooooo oooooooo`  
`Num plain text limit: 0-3`  
`Num to copy limit:    4-67`  
`Maximum Offset:       16384`

### 0xC0 - 0xDF

This format differs depending on the game.

#### Sims 2

`CC length:      4 bytes`  
`Num plain text: byte0 & 0x03`  
`Num to copy:    ( (byte0 & 0x0C) < < 6 )  + byte3 + 5`  
`Copy offset:    ((byte0 & 0x10) < < 12 ) + (byte1 < < 8 ) + byte2 + 1`

`Bits: 110occpp oooooooo oooooooo cccccccc`  
`Num plain text limit: 0-3`  
`Num to copy limit:    5-1028`  
`Maximum Offset:       131072`

#### SimCity 4

Remark: This format does *not* seem to be used by SimCity 4 (Deluxe?). Instead, the format above is used.

`CC length:      4 bytes`  
`Num plain text: byte0 & 0x03`  
`Num to copy:    ( (byte0 & 0x1C) < < 6 )  + byte3 + 5`  
`Copy offset:    (byte1 < < 8) + byte2`

`Bits: 110cccpp oooooooo oooooooo cccccccc`  
`Num plain text limit: 0-3`  
`Num to copy limit:    5-2047`  
`Maximum Offset:       65535`

### 0xE0 - 0xFB

`CC length:      1 byte `  
`Num plain text: ((byte0 & 0x1F) < < 2 ) + 4`  
`Num to copy:    0 `  
`Copy offset:    - `

`Bits: 111ppppp `  
`Num plain text limit: 4-112 `  
`Num to copy limit:    0 `  
`Maximum Offset:       -`

### 0xFC - 0xFF

`CC length:      1 byte `  
`Num plain text: (byte0 & 0x03)`  
`Num to copy:    0 `  
`Copy offset:    - `

`Bits: 111111pp `  
`Num plain text limit: 0-3 `  
`Num to copy limit:    0 `  
`Maximum Offset:       -`

## Example Code

See Wouangaine's [C library](https://github.com/wouanagaine/SC4Mapper-2013/blob/master/Modules/qfs.c) for QFS compression. It's much more likely to work than the below PHP code.

This is written in PHP, converted from Perl code by dmchess mentioned in [this forum thread](http://hullabaloo.simshost.com/forum/viewtopic.php?t=6578&postdays=0&postorder=asc).

`// First, we read in the length of the total compressed data.`  
`// read_UL4 is a PHP function in my DBPF class that grabs the`  
`// next 4 bytes and uses unpack to convert to a integer.`  
`$len = $this->read_UL4($handle);`  
  
`// Read the next 5 bytes (they are not used in this code,`  
`// and are simply read and stashed out of the way).`  
`$garbagedata = fread($handle, 5);`  
  
`// Decompress the chunk.`  
`// We do $len - 9 here because we are ignoring the first 9 bytes`  
`// of the chunk (4 for the length value itself, 5 for other data).`  
`// See later for a description of $this->decompress.`  
`$data = $this->decompress($handle, $len - 9);`  
  
`// ** Internally used I/O functions`  
  
`// Reads a 4 byte unsigned integer`  
`/*`  
`       Used internally by the class to read a C/C++ "unsigned long"`  
`       (a 4 byte unsigned integer) from an open file`  
`       $fh - the file handle from which to read`  
`       returns - returns the value read; has no error return`  
`*/`  
`function read_UL4($fh)`  
`{`  
`       $d = fread($fh, 4);`  
`       $a = unpack("Vn", $d);`  
`       return $a["n"];`  
`}`  
  
`// Reads a 2 byte unsigned integer`  
`/*`  
`       Used internally by the class to read a C/C++ "unsigned short"`  
`       (a 2 byte unsigned integer) from an open file`  
`       $fh - the file handle from which to read`  
`       returns - returns the value read; has no error return`  
`*/`  
`function read_UL2($fh)`  
`{`  
`       $d = fread($fh, 2);`  
`       $a = unpack("vn", $d);`  
`       return $a["n"];`  
`}`  
  
`// Reads a 1 byte unsigned integer`  
`/*`  
`       Used internally by the class to read a C/C++ "unsigned char"`  
`       (a 1 byte unsigned integer) from an open file`  
`       $fh - the file handle from which to read`  
`       returns - returns the value read; has no error return`  
`*/`  
`function read_UL1($fh)`  
`{`  
`       $d = fread($fh, 1);`  
`       $a = unpack("Cn", $d);`  
`       return $a["n"];`  
`}`  
  
`// Decompression function applied to string:`  
`/*`  
`       PHP DBPF decompression by Delphy`  
`       Thanks to dmchess (see link above)`  
`       for the Perl code used for this`  
`       $handle - file handle for reading`  
`       $len - length of compressed string`  
`*/`  
`       function decompress($handle, $len) {`  
`               $buf = '';`  
`               $answer = "";`  
`               $answerlen = 0;`  
`               $numplain = "";`  
`               $numcopy = "";`  
`               $offset = "";`  
`       `  
`       // Main loop:`  
`               for (;$len>0;) {`  
`                       $cc = $this->read_UL1($handle);`  
`                       $len -= 1;`  
`               //      printf("      Control char is %02x, len remaining is %08x. \n",$cc,$len);`  
`                       if ($cc >= 252): // 0xFC`  
`                               $numplain = $cc & 0x03;`  
`                               if ($numplain > $len) { $numplain = $len; }`  
`                               $numcopy = 0;`  
`                               $offset = 0;`  
`                       elseif ($cc >= 224): // 0xE0`  
`                               $numplain = ($cc - 0xdf) << 2;`  
`                               $numcopy = 0;`  
`                               $offset = 0;`  
`                       elseif ($cc >= 192): // 0xC0`  
`                               $len -= 3;`  
`                               $byte1 = $this->read_UL1($handle);`  
`                               $byte2 = $this->read_UL1($handle);`  
`                               $byte3 = $this->read_UL1($handle);`  
`                               $numplain = $cc & 0x03;`  
`                               $numcopy = (($cc & 0x0c) <<6) + 5 + $byte3;`  
`                               $offset = (($cc & 0x10) << 12 ) + ($byte1 << 8) + $byte2;`  
`                       elseif ($cc >= 128): // 0x80`  
`                               $len -= 2;`  
`                               $byte1 = $this->read_UL1($handle);`  
`                               $byte2 = $this->read_UL1($handle);`  
`                               $numplain = ($byte1 & 0xc0) >> 6;`  
`                               $numcopy = ($cc & 0x3f) + 4;`  
`                               $offset = (($byte1 & 0x3f) << 8) + $byte2;`  
`                       else:`  
`                               $len -= 1;`  
`                               $byte1 = $this->read_UL1($handle);`  
`                               $numplain = ($cc & 0x03);`  
`                               $numcopy = (($cc & 0x1c) >> 2) + 3;`  
`                               $offset = (($cc & 0x60) << 3) + $byte1;`  
`                       endif;`  
`                       $len -= $numplain;`  
  
`               // This section basically copies the parts of the string to the end of the buffer:`  
`                       if ($numplain > 0) {`  
`                               $buf = fread($handle, $numplain);`  
`                               $answer = $answer.$buf;`  
`                       }`  
`                       $fromoffset = strlen($answer) - ($offset + 1);  # 0 == last char`  
`                       for ($i=0;$i<$numcopy;$i++) {`  
`                               $answer = $answer.substr($answer,$fromoffset+$i,1);`  
`                       }`  
`                       $answerlen += $numplain;`  
`                       $answerlen += $numcopy;`  
`               }`  
  
`               // Return the decompressed string back:`  
`               return $answer;`  
`       }`

## Other References

`/*------------------------------------------------------------------*/`  
`/*                                                                  */`  
`/*               RefPack - Backward Reference Codex                 */`  
`/*                                                                  */`  
`/*                    by FrANK G. Barchard, EAC                     */`  
`/*                                                                  */`  
`/*------------------------------------------------------------------*/`  
`/* Format Notes:                                                    */`  
`/* -------------                                                    */`  
`/* refpack is a sliding window (131k) lzss method, with byte        */`  
`/* oriented coding.                                                 */`  
`/*                                                                  */`  
`/* huff fb5 style header:                                           */`  
`/*      *10fb  fb5      refpack 1.0  reference pack                 */`  
`/*                                                                  */`  
`/*                                                                  */`  
`/* header:                                                          */`  
`/* [10fb] [unpacksize] [totalunpacksize]                            */`  
`/*   2         3                                                    */`  
`/*                                                                  */`  
`/*                                                                  */`  
`/*                                                                  */`  
`/* format is:                                                       */`  
`/* ----------                                                       */`  
`/* 0ffnnndd_ffffffff          short ref, f=0..1023,n=3..10,d=0..3   */`  
`/* 10nnnnnn_ddffffff_ffffffff long ref, f=0..16384,n=4..67,d=0..3   */`  
`/* 110fnndd_f.._f.._nnnnnnnn  very long,f=0..131071,n=5..1028,d=0..3*/`  
`/* 111ddddd                   literal, d=4..112                     */`  
`/* 111111dd                   eof, d=0..3                           */`  
`/*                                                                  */`  
`/*------------------------------------------------------------------*/`

From <http://download.wcnews.com/files/documents/sourcecode/shadowforce/transfer/asommers/mfcapp_src/engine/compress/RefPack.cpp>

See Also: <http://wiki.niotso.org/RefPack>
