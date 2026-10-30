---
title: "Advice Subfiles"
description: ""
published: false
date: '2019-08-10T01:25:32Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:25:32Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Advice** files within [Savegame](/savegame) files.

## Specifications

### Template-All Advices/Advisors 8a09f5f4

`Dword - File size of Section.`  
`14 bytes - Unknown`  
`Dword - Advice Message Resource.`  
`Dword - Unknown`  
`Dword - Advice ID (Can/May also include Advisor ID (values)).`  
`Dword - Advice Priority.`  
`Dword - Advice Frequency.`  
`Dword - Advice Timeout (in days). `  
`Dword - Advice Moods.`  
`Dword - Equals the number of ("Extended & Repeated") Dwords that follow.`  
`XxDword - See Dword above to get the number of Dwords here - Unknown.`  
`Dword - Unknown.`

And repeat throughout file. The end of the whole file ends with the end of a section.

### MySim 6a9335de

`Dword - File size of Section.`  
`14 bytes - Unknown`  
`Dword - Advice Message Resource.`  
`Dword - Unknown`  
`Dword - Advice ID (Can/May also include Advisor ID (values)).`  
`Dword - Advice Priority.`  
`Dword - Advice Frequency.`  
`Dword - Advice Timeout (in days). `  
`Dword - Advice Moods.`  
`8 Bytes - Unknown`

And repeat throughout file. The end of the whole file ends with the end of a section.

### MySim 6b70efad

`Dword - File size of Section.`  
`14 Bytes - Unknown`  
`Dword - Advice Message Resource.`  
`Dword - Unknown`  
`Dword - Advice ID (Can also include Advisor ID (values)).`  
`Dword - Advice Priority.`  
`Dword - Advice Frequency.`  
`Dword - Advice Timeout (in days). `  
`Dword - Advice Moods.`  
`8 Bytes - Unknown`

And repeat throughout file. The end of the whole file ends with the end of a section.

### City Situations 8be3753b

`Dword - File size of Section.`  
`14 bytes - Unknown`  
`Dword - Advice Message Resource.`  
`Dword - Unknown`  
`Dword - Advice ID (Can/May also include Advisor ID (values)).`  
`Dword - Advice Priority.`  
`Dword - Advice Frequency.`  
`Dword - Advice Timeout (in days). `  
`Dword - Advice Moods.`  
`Dword - Unknown.`  
`X Bytes - Unknown (number of bytes equals the remainder of the file).`  
`          It's mostly 4 bytes left though.`

And Repeat throughout file. The end of the whole file ends with the end of a section.

### Utilities-Neighbour Deals 6a3848db

`Dword - File size of Section.`  
`16 bytes - Unknown`  
`Dword - Advice Message Resource.`  
`Dword - Unknown`  
`Dword - Advice ID (Can/May also include Advisor ID (values)).`  
`Dword - Advice Priority.`  
`Dword - Advice Frequency.`  
`Dword - Advice Timeout (in days).`  
`Dword - Advice Moods.`  
`8 Bytes - Unknown`  
`Dword - Neighbour Deal ID.`

And Repeat throughout file. The end of the whole file ends with the end of a section.

### Reward aa371c32

Undecoded and not wholly confirmed.
