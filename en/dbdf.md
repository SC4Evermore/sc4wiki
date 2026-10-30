---
title: "DBDF"
description: ""
published: true
date: '2023-03-20T23:38:07Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2008-09-21T18:20:17Z'
---

**DBDF** files (DataBase Directory Files, commonly referred to as just Directory or DIR files) are directories of all of the compressed files within a [DBPF](/dbpf) file. As such, a DBPF will contain a DBDF if any of its subfiles are compressed. The purpose of these resources is to speed up the loading of a DAT file by showing exactly what is compressed inside it. The [TGI](/tgi) for a DBDF is always *E86B1EEF E86B1EEF 286B1F03*.

## Format

DBDF files contain repeating 16 byte chunks giving information about a given subfile within the DBPF. In the DBPF version used in [SimCity 4](/simcity-4), with index table version 7.0, the format is as follows.

`DWORD - `[<code>Type ID</code>](/type-id)` of file`  
`DWORD - `[<code>Group ID</code>](/group-id)` of file`  
`DWORD - `[<code>Instance ID</code>](/instance-id)` of file`  
`DWORD - Size of file when decompressed, in bytes.`

In DBPF's with version 7.1 index tables, the repeating chunk is 20 bytes, and it contains an entry for the Resource ID of the file (after the IID, before the size). This format is not used by SC4, but is mentioned here for completeness.

## Notes

It is *strongly* recommended that you update the DBDF after editing any compressed file, and before saving the .dat if you are working manually in hex or making your own program.
