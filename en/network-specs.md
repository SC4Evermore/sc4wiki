---
title: "Network Specs"
description: ""
published: false
date: '2019-08-04T06:00:49Z'
tags: ["NAM", "Transit Modding", "Network Specs"]
editor: markdown
dateCreated: '2008-10-27T19:25:11Z'
---

## Preface

This page is the introduction to the **Network Specs** document, written by [Tropod](/people/tropod), which has been copied over to the Wiki for safekeeping and preservation. This document can also be found in an attachment to the [NAM Inner Workings](http://sc4devotion.com/forums/index.php?topic=5560.0) thread at [SimCity 4 Devotion](/simcity-4-devotion). *Much of the information contained in this document is known to be outdated*, it is not advised to use this document as the sole reference for transit modding. More current and accurate information can be found in other parts of this Wiki - for example the pages in the [Transit Modding](/category/transit-modding) and [Transit Networks](/category/transit-networks) Categories. The original document begins below.

## Network Specs Introduction

A lot of information contained in these files are extracts from the [Simtropolis](/simtropolis) website, from both of the Modding forums. Some information has been extracted from the games own files. Various persons have helped in the deciphering, contribution, and/or gathering of this information. Most notably, , , , , and others. While the specs covered go into great detail and cover quite a lot about [SimCity 4](/simcity-4) networks, it is not completely comprehensive and may contain errors and/or omissions and/or out of date techniques.

Lets begin shall we...

In total there are 32 [RUL Files](/rul-file) that (originally) come with the game ([Rush Hour](/rush-hour) version). There is also a [INI Network-based file](/network-ini). These files (and others) govern how the different networking aspects in SimCity 4 are controlled (or drawn/built in-game). Out of the 32 original RUL files and INI file, some of them have a specific functionality about them and/or in them for the networks. These aspects will be covered in some detail. Follow the links below to a specific area.

1.  
2.  
3.  
4.  
5.  
6.  
7.  

**Please note:**

- RUL/INI files are essentially referenced by the EXE. Therefore, unless the address of a RUL file already exists within the EXE, it can not function. In other words, "new" RULs can not be added without it already having been defined and/or existing in the EXE. And thus, new networks can not be added.
- Items, names, and functions in <font color="green">green</font> are typically actual valid code and/or are from the relative RUL/INI abd/or other files.

------------------------------------------------------------------------

<div align=center>

**Disclaimer**

The contents of this document are in no way supported nor endorsed by Maxis or Electronic Arts Incorporated (EA). SimCity 4, SimCity 4 Rush Hour EP, SimCity 4 Deluxe, and associated materials and tools are the property of Electronic Arts Incorporated. The format of any files mentioned in this document belong to Maxis and/or other respective parties. The creator of this document, and the many persons involved with the aspects that this document covers, are not responsible or liable for any loss incidental or otherwise that may arise from the use of this document and the information contained within. The use of this document and the information within it is used solely at your own risk. The use of this document is conditional and acceptance of this disclaimer and all that is within this document.

</div>
