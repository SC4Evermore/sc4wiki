---
title: "DBPF"
description: ""
published: false
date: '2025-05-21T11:49:06Z'
tags: ["File Formats/SC2013", "File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2008-09-20T16:05:56Z'
---

**Database Packed File (DBPF)** is a proprietary archive format used in many Maxis developed games, including The Sims 2, [SimCity 4](/simcity-4) and Spore. DBPF files are similar to Zip files, as they hold other files inside them which are usually compressed. All plugins for SimCity 4 (excluding the [SC4 Extra Cheats.dll](/plugin/sc4-extra-cheats-dll)) are DBPF files, the file name's extension is irrelevant. Note that [savegame](/savegame) (.sc4) files are also DBPF files. DBPF files are sometimes referred to as *packages* following the convention used in The Sims 2, where the files sometimes have the .package file extension.

DBPF files can be identified by opening the file in notepad, or preferably a hex editor, as the first 4 characters/bytes will be the letters DBPF. If a file in the plugins folder does not start with these 4 letters the game will not load them, however the [Reader](/reader) will. This means that if you want to disable a plugin you can open the DBPF file in a hex editor and change the first byte to something other than 44 (in Hexadecimal) (D) and the game will not load the plugin, but you will still be able to edit it in the reader (saving the disabled plugin with the reader will not re enable it, to re enable you must change the first byte back to 44 (hexadecimal)).

Entries may be compressed with RefPack/[QFS compression](/qfs-compression) depending on their entry data.

For an examination of the Spore DBPF format, see [Spore DBPF](/spore-dbpf).

## Format

### Overview

This is the general structure of Database Packed File packages:

`Header (96 bytes)`  
`File 1`  
`File 2`  
`...`  
`File n`  
`Index Entry 1`  
`Index Entry 2`  
`...`  
`Index Entry n `

Header first, individual files following with no file names and a small file header area at the beginning of each, followed by an index of all the files in the archive. Note that files may appear after the index table in files that are updated.

### Header

<table style="width:19%;">
<colgroup>
<col style="width: 5%" />
<col style="width: 2%" />
<col style="width: 5%" />
<col style="width: 1%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr>
<th width="5%"><p>Offset</p></th>
<th width="20%"><p>Name</p></th>
<th width="5%"><p>Version</p></th>
<th width="10%"><p>Type/Size</p></th>
<th width="60%"><p>Info</p></th>
</tr>
</thead>
<tbody>
<tr>
<td><p>00</p></td>
<td><p>Identifier</p></td>
<td></td>
<td><p>char[4]</p></td>
<td><p>DBPF</p></td>
</tr>
<tr>
<td><p>04</p></td>
<td><p>Major Version</p></td>
<td></td>
<td><p>u32</p></td>
<td rowspan="2"><ul>
<li>1.0 seen in Sim City 4, The Sims 2</li>
<li>1.1 seen in The Sims 2</li>
<li>2.0 seen in Spore, The Sims 3</li>
<li>3.0 seen in SimCity</li>
</ul></td>
</tr>
<tr>
<td><p>08</p></td>
<td><p>Minor Version</p></td>
<td></td>
<td><p>u32</p></td>
</tr>
<tr>
<td><p>12</p></td>
<td><p>User Major Version</p></td>
<td></td>
<td><p>u32</p></td>
<td rowspan="2"><p>Additional version field that can be used by the game, e.g., for rejecting save files made by a newer game version. Separate from the DBPF file format version. Possibly unused.</p></td>
</tr>
<tr>
<td><p>16</p></td>
<td><p>User Minor Version</p></td>
<td></td>
<td><p>u32</p></td>
</tr>
<tr>
<td><p>20</p></td>
<td><p>unknown</p></td>
<td><p>2.0</p></td>
<td><p>u32</p></td>
<td><p>Should always be zero in DBPF 2.0.</p></td>
</tr>
<tr>
<td><p>24</p></td>
<td><p>Date Created</p></td>
<td><p>1.0</p></td>
<td><p>u32</p></td>
<td><p>in Unix time stamp format (the number of seconds since 1/1/1970) (Unused in Version 1.1)</p></td>
</tr>
<tr>
<td><p>28</p></td>
<td><p>Date Modified</p></td>
<td><p>1.0</p></td>
<td><p>u32</p></td>
<td><p>in Unix time stamp format (the number of seconds since 1/1/1970) (Unused in Version 1.1)</p></td>
</tr>
<tr>
<td><p>32</p></td>
<td><p>Index major version</p></td>
<td><p>&lt; 2.0</p></td>
<td><p>u32</p></td>
<td><p>Always 7 in The Sims 2, Sim City 4. If this is used in 2.0, then it is 0 for SPORE.</p></td>
</tr>
<tr>
<td><p>36</p></td>
<td><p>Index entry count</p></td>
<td></td>
<td><p>u32</p></td>
<td><p>Number of entries in the Index Table.</p></td>
</tr>
<tr>
<td><p>40</p></td>
<td><p>Offset of first Index entry</p></td>
<td><p>&lt; 2.0</p></td>
<td><p>u32</p></td>
<td><p>Location of first index entry</p></td>
</tr>
<tr>
<td><p>44</p></td>
<td><p>Index size</p></td>
<td></td>
<td><p>u32</p></td>
<td><p>Size of the Index table, in bytes.</p></td>
</tr>
<tr>
<td><p>48</p></td>
<td><p>Hole entry count</p></td>
<td><p>&lt; 2.0</p></td>
<td><p>u32</p></td>
<td><p>Number of Hole entries in the Hole Record</p></td>
</tr>
<tr>
<td><p>52</p></td>
<td><p>Hole offset</p></td>
<td><p>&lt; 2.0</p></td>
<td><p>u32</p></td>
<td><p>Location of the hole Record</p></td>
</tr>
<tr>
<td><p>56</p></td>
<td><p>Hole size</p></td>
<td><p>&lt; 2.0</p></td>
<td><p>u32</p></td>
<td><p>Size of the hole Record</p></td>
</tr>
<tr>
<td><p>60</p></td>
<td><p>Index minor version</p></td>
<td><p>&lt; 2.0?</p></td>
<td><p>u32</p></td>
<td><p>01 = 7.0, 02 = 7.1, Version 1.1+ in The Sims 2 only. In DBPF 2.0, it has a value of 03, unknown if used.</p></td>
</tr>
<tr>
<td><p>64</p></td>
<td><p>Index offset</p></td>
<td><p>2.0</p></td>
<td><p>u32</p></td>
<td><p>Offset to Index table in DBPF 2.0.</p></td>
</tr>
<tr>
<td><p>68</p></td>
<td><p>unknown</p></td>
<td><p>2.0</p></td>
<td><p>u32</p></td>
<td></td>
</tr>
<tr>
<td><p>72</p></td>
<td><p>reserved</p></td>
<td></td>
<td><p>char[24]</p></td>
<td><p>Reserved for use in future versions.</p></td>
</tr>
</tbody>
</table>

### Index Table

There are two known formats of indexes in the game. The format version is found in the file header. Index Tables list the contents of the DBPF package, giving the information below depending on the Index Table version used.

A third format has been discovered, and is used in The Sims 2, but the structure is currently unknown. The Index Minor Version is an actual zero, so this would be called "Index Table 7.-1" by the logic used here. This format has been seen in files that ship with that game, and is believed to have been seen in files generated by that game, but has not yet been seen in user-created files (for obvious reasons). These files were discovered by the simple expedient of having a file-scanning tool choke on them during a scan of the entire game.

The index table is very similar to the directory file ([DIR](/dir)) within a DPBF package. The difference being that the Index Table lists *every* file in the package, whereas the directory file only lists the compressed files within the package. [Reader](/reader) presents a directory file that is a mashup of these two entities, listing every file in the package, as well as indicating whether or not that particular file is compressed.

#### DBPF 1.x, Index Table 7.0

(20 bytes, some DBPF 1.1 entries use this format) A typical entry in this table looks like:

**`DWORD`**  
` Type ID`  
**`DWORD`**  
` Group ID`  
**`DWORD`**  
` Instance ID`  
**`DWORD`**  
` Location of the file in the archive `  
**`DWORD`**  
` Size of the file `

#### DBPF 1.x, Index Table 7.1

(24 bytes) A typical entry in this table looks like:

**`DWORD`**  
` Type ID`  
**`DWORD`**  
` Group ID`  
**`DWORD`**  
` Instance ID`  
**`DWORD`**  
` Second Instance ID (a.k.a. Resource ID)(Not used in SimCity 4, but is used for GUID Based systems in The Sims 2)`  
**`DWORD`**  
` Location of the file in the archive `  
**`DWORD`**  
` Size of the file`

### Hole Table

A Hole Table contains the location and size of all holes in a DBPF file. Holes are created when the game deletes something from a DBPF. The holes themselves are simply junk data of the appropriate length to fill the hole.

#### DBPF 1.x

(8 bytes) A typical entry in this table looks like:

**`DWORD`**  
` Hole Location`  
**`DWORD`**  
` Hole size`

## Files Within DBPF Files

The files included in a DBPF file make up the bulk of the DBPF package. Each file is either uncompressed or compressed. To check if a file is compressed you first need to read the [DIR](/dir) file, if it exists. If no DIR entry exists, then no files within the package are compressed.

### Directory File

The directory file ([DIR](/dir)) is included in DBPF files whenever there are compressed files within the package.

### Compression

When reading a DBPF file, the first thing you should do is check to see if any chunks inside are compressed. This is done via the [DIR](/dir) (E86B1EEF) resource. For example code and a description of the mechanics, see [DBPF Compression](/dbpf-compression).

### File Header

(9 bytes) The file header only exists if the file is compressed, and looks like this:

**`DWORD`**  
` Compressed Size of file`  
**`WORD`**  
` Compression ID (0x10FB) QFS Compression. (See `[<code>DBPF Compression</code>](/dbpf-compression)` for more information)`  
**`3 bytes`**  
` Uncompressed size of the file`

### Body

Raw data of the files, may be compressed or uncompressed. See [List of File Formats](/list-of-file-formats) for a list of the file types that may exist within a DBPF file.

## Pseudocode

To read files inside a DBPF file, you need to perform the following steps, in order:

- Read the DBPF header.
- Read the Index Tables.
- Check for a DIR record.
- Check for the file you want to extract.
- Is this file compressed? If so, decompress it.
- Read the file data and process accordingly.

For an example PHP class for reading DBPF files, see [DBPF Source Code](/dbpf-source-code)

## Visual Format Guide

These visual guides to the DBPF file format were created by [DarkMatter](/people/darkmatter):

<table>
<tbody>
<tr>
<td><figure>
<img src="/images/DBPF_File_Format_v1.1.png" title="DBPF v1.x" width="200" height="152" />
<figcaption>DBPF v1.x</figcaption>
</figure></td>
<td><figure>
<img src="/images/DBPF_File_Format_v2.0.png" title="DBPF v2.0" width="200" height="152" />
<figcaption>DBPF v2.0</figcaption>
</figure></td>
</tr>
</tbody>
</table>

Some information was taken from old DatGen source code, such as the Created/Modified timestamps and possible Flags DWORD. That information may not be accurate, per DarkMatter's own description. Reason given is that it was some time ago that he "last chatted with Maxoids about the DBPF format."
