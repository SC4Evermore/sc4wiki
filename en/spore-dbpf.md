---
title: "Spore DBPF"
description: ""
published: true
date: '2019-08-04T05:40:59Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-08T23:16:00Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

The following contains information about the [DBPF](/dbpf) file type used for the Maxis game **Spore**. It was copied from [CustomSims3](http://www.customsims3.com/forum1/YaBB.pl?num=1214408105) *(Editor's note: as of Sept. 8, 2012, that page was 404 error)*.

    // File Format Specs
    // Header:
    //    DWord type_name [0x46504244 "DBPF"]
    //    DWord version_maj [2]
    //    DWord version_min [0]
    //    DWord ???
    //    DWord ???
    //    DWord ???
    //    DWord ??? [created?]
    //    DWord ??? [modified?]
    //    DWord ??? [index_maj?]
    //    DWord entry_count
    //    Dword old_version_field [formerly the entry point]
    //    DWord index_size  [index size]
    //    Dword ??? [num_holes?]
    //    Dword ??? [hole_loc?]
    //    Dword ??? [hole_size?]
    //    Dword ??? [index_min?] [3]
    //    DWord index_start_V2 [file offset to seek to for index start]
    //    DWord padding[7]
    //
    // Index:
    // In general, a single linear read of this file type is impossible.
    // You have to read the index, often (but not necessarily) located at the end of the file.
    // So, you can read the header, skip to the index, sort the entries, rewind and skip to
    // each chunk, or you can seek from each index entry to the chunk, then return to the index.
    //
    //    DWord index_type [known values 4, 5, 6 and 7]
    //
    //    case 4:  [8+(entry_count*28) must equal index_size]
    //    DWord index_null [zero]
    //    repeated once per entry_count:
    //      DWord type
    //      DWord group?
    //      DWord instance?
    //      DWord Chunk_offset
    //      DWord Disk_Size [or'd with 0x80000000]
    //      DWord Mem_size [decompressed size]
    //      Word Compressed [0=no, 0xFFFF=yes]
    //      Word unknown [1]
    //    case 5:    [12+(entry_count*24) must equal index_size]
    //    DWord type
    //    DWord index_null [zero]
    //    repeated once per entry_count:
    //      DWord group?
    //      DWord instance?
    //      DWord Chunk_offset
    //      DWord Disk_Size [or'd with 0x80000000]
    //      DWord Mem_size [decompressed size]
    //      Word Compressed [0=no, 0xFFFF=yes]
    //      Word unknown [1]
    //    case 6:    [12+(entry_count*24) must equal index_size]
    //    DWord type
    //    DWord index_null [zero]
    //    repeated once per entry_count:
    //      DWord group?
    //      DWord instance?
    //      DWord Chunk_offset
    //      DWord Disk_Size [or'd with 0x80000000]
    //      DWord Mem_size [decompressed size]
    //      Word Compressed [0=no, 0xFFFF=yes]
    //      Word unknown [1]
    //    case 7:    [16+(entry_count*20) must equal index_size]
    //    DWord type
    //    DWord group?
    //    DWord index_null [zero]
    //    repeated once per entry_count:
    //      DWord instance?
    //      DWord Chunk_offset
    //      DWord Disk_Size [or'd with 0x80000000]
    //      DWord Mem_size [decompressed size]
    //      Word Compressed [0=no, 0xFFFF=yes]
    //      Word unknown [1]
    //
    // The overall structure appears that index type 4 has a unique type, group and instance
    // for each entry, index types 5 and 6 all share the same type, and index type 7 all
    // share the same type and group values. So 5, 6 and 7 are shorter per entry to save space
    //
    // Chunks:
    //    Every chunk type is different. The index entry tells you where in the file the
    //    chunk starts at, and how large it is. If it is compressed, the index gives the
    //    uncompressed size. The compression is compatible with that used for DBPF V1, but
    //    the compressed file header has changed from 9 bytes to 5. These 5 bytes are
    //    counted as a part of the compressed size indicated in the index. The first two bytes
    //    are the compression type 0x10, 0xFB or 0x50, 0xFB [0xFB10 or 0xFB50]. These appear
    //    to decompress the same way. The next three bytes are the decompressed size, in
    //    Big-Endian format (hi-byte to lo-byte). This should match the value found in the
    //    index. Examples of decompression code are documented on the Sims2Wiki and at
    //    moreawesomethanyou.com.
    //

See also [Spore:Chunk Types](http://simswiki.info/wiki.php?title=Spore:Chunk_Types).

## Visual Guide to DBPF v2.0

These below visual guides to the DBPF file format v2 was created by [DarkMatter](/people/darkmatter):

<table>
<tbody>
<tr>
<td><figure>
<img src="/_files/images/dbpf-file-format-v2-0.png" title="DBPF v2.0" width="200" height="152" />
<figcaption>DBPF v2.0</figcaption>
</figure></td>
</tr>
</tbody>
</table>

Some information was taken from old DatGen source code, such as the Created/Modified timestamps and possible Flags DWORD. That information may not be accurate, per DarkMatter's own description. Reason given is that it was some time ago that he "last chatted with Maxoids about the DBPF format."
