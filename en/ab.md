---
title: "AB"
description: ""
published: true
date: '2019-08-09T02:54:45Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-04T21:35:54Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**AB** File Structure:

`Offset    Length   Description`  
`------    -------   ----------------------------------------------------------------------------`  
`+00       4         File ID. First two bytes define "AB", full ID is 0x41420900`  
`+04       4         File size in bytes.`  
`+08       4         Unknown ID. First two bytes define "EI", full ID is 0x45491800`  
`+44       4         Unknown 1. First byte always defines "T", full ID is 0x54000000`

Aside from these DWORDs that are always the same in every AB file, each one seems to have several distinct sections. The pattern of data changes periodically as you scroll through (AB files are very large), although the number of unique sections has not been counted or defined.
