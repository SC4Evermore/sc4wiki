---
title: "AE"
description: ""
published: false
date: '2019-08-09T02:54:45Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-04T23:11:00Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**AE** files contian [U-Drive-It](/u-drive-it) settings.

## Specification

The format of the AE files is as follows. The basic structure of the file is listed below, however much work remains to figure out what all these parts are and what they do.

### Header (8 bytes)

`WORD`  
`WORD`  
`WORD`  
`WORD - Size of the Index`

### Index

`WORD  - Section 1 Count`  
`WORD  - Section 2 Count`  
`WORD  - Section 3 Count`  
`WORD  - Section 4 (Table) Count`  
`DWORD - Section 1 Offset`  
`DWORD - Section 2 Offset`  
`DWORD - Section 3 Offset`  
`DWORD - Section 4 Offset`

### Section 1

This section consists of repeating 24 byte chunks.

     DWORD
     DWORD
     WORD
     WORD
     DWORD
     WORD
     WORD
     WORD
     WORD

### Section 2

This section consists of repeating 16 byte chunks.

     WORD
     WORD
     DWORD
     WORD
     WORD
     WORD
     WORD

### Section 3

This section consists of repeating 32 byte chunks.

     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD
     DWORD

### Section 4 (Tables)

This section consists of three tables. The first and second are 1024 bytes long each. The third is 484 bytes.

`DWORD x 256 (for first 2)`  
`or`  
`DWORD x 121 (for the third)`

After the tables, comes info about how many times the tables repeat.

`DWORD`  
`DWORD (I Count++)`

Add up the value of all ICounts from the Aftertables to get the count of DWORDS here.

`DWORD x ICount`
