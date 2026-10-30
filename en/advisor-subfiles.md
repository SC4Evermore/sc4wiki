---
title: "Advisor Subfiles"
description: ""
published: false
date: '2019-08-05T02:23:12Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2012-09-16T00:57:43Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Advisors** files within [Savegame](/savegame) files.

NOTE: *\[Start Break\]* notes the start of a section where there are repeating sections. *\[End Break\]* notes the end of the section where there are repeating sections.

Repeating sections can/do exist in multiple locations, and also within an already repeating section in the one file. Where this occurs, this section has been noted by its "Break Number" - For example:

`[Start Break 'Number Here']`  
`...file/section data here...`  
`[End Break 'Number here']`

## Specifications

Following are the specifications for the various Advisor files.

### My Street Sim 0bf606a5

`Dword - File size of section.`  
`17 Bytes - Unknown`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Unknown`  
`Dword - Unknown`  
`Dword - Unknown`  
`Dword - Advisor ID.`  
`Dword - Unknown`  
`Dword - Unknown`  
  
`[start break]`  
`  Dword - Unknown. Often changes.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown.`  
`  Dword - Unknown. `  
`  Dword - Unknown. `  
`  Byte - Unknown.`  
`  Dword - Often has a specific Advisor Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - Remaining at end of file after repeating section above.`

### City Planner 2A5F877D

`Dword - File size of section.`  
`16 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name. `  
`String - Section Name. (Advisor Name)`  
`Dword - Unknown`  
`Dword - Unknown`  
`Dword - Advisor ID.`  
`Dword - Unknown`  
`Dword - Unknown`  
  
`[start break]`  
`  Dword - Unknown. Often changes, though usually not by much when it does.`  
`  Dword - Advisor Message Category/Group [Class ID].`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  Byte - Unknown.`  
`  Dword - May or may not have a specific (Advisor) Message ID Value here, mostly 00000000 though.`  
`          (Found the "NEW_CITY game event" Advisor  Message in this file).`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`X bytes - remaining at end of file after repeating section above - Unknown.`

### MySim 4A1DBBBF

File contains "MySim" 1/2/3/4/5.

`[start break ONE]`  
`  Dword - File Size of Section. `  
`  17 bytes - Unknown.`  
`  Dword - Length of Section Name.`  
`  Dword - Section Name (The different advisor departments).`  
`  Dword - Unknown`  
`  Dword - Unknown`  
`  Dword - Unknown`  
`  Dword - Advisor ID.`  
`  Dword - Unknown`  
`  Dword - Unknown`  
`  [start break TWO]`  
`    Dword - Unknown`  
`    Dword - Advisor Message Category/Group (Class ID).`  
`    Dword - Unknown`  
`    Dword - Unknown`  
`    Dword - Unknown`  
`    byte - Unknown.`  
`    Dword - May or may not have a specific (Advisor) Message ID Value here, mostly 00000000 though.`  
`  [end break TWO]`  
`  (And then repeat throughout section as per above.)`  
  
`  Dword [00000000] - remaining at end of the section after repeating section above.`  
`[end break ONE] `

And then repeat the WHOLE section above for MySim2/3/4/5.

### Transportation 4A3AD3E1

`Dword - Number of Bytes.`  
`14 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name.`  
`String - Section Name (Advisor Name)`  
`Dword - Unknown`  
`Dword - Unknown.`  
`Dword - Advisor ID.`  
`Dword - Unknown.`  
`Dword - Unknown.`  
  
`[start break]`  
`  Dword - Unknown, often changes.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown, 00000000?? Often Changes.`  
`  Dword - Unknown, FB010000?? Often Changes.`  
`  Dword - Unknown.`  
`  Byte - Unknown.`  
`  Dword - Often has a specific (Advisor) Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - remaining at end of file after repeating section above.`

### City Situations 4BE372CD

`Dword - File size.`  
`14 bytes - Unknown`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name`  
`String - Section Name (Advisor Name)`  
`Dword - Unknown.`  
`Dword - Unknown.`  
`Dword - Advisor ID.`  
`Dword - Unknown`  
`Dword - Unknown`  
  
`[start break]`  
`  Dword - Unknown, often changes.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown. Often changes.`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  byte - Unknown. (Found a file/byte where it is 01).`  
`  Dword - Unknown.`  
`[End break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] remaining at end of file after repeating section above.`

### Health and Education 6A5F8755

`Dword - File size of section.`  
`14 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name.`  
`String - Section Name  (Advisor Name)`  
`Dword - Unknown`  
`Dword - Unknown`  
`Dword - Advisor ID.`  
`Dword - Unknown`  
`Dword - Unknown`  
  
`[start break]`  
`  Dword - Unknown`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown`  
`  Dword - Unknown`  
`  Dword - Unknown`  
`  byte - Unknown`  
`  Dword - Often has a specific (Advisor) Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - remaining at end of file after repeating section above.`

### Finances AA5292D7

`Dword - File size of section.`  
`14 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name.`  
`String - Section Name  (Advisor Name)`  
`Dword - Unknown.`  
`Dword - Unknown.`  
`Dword - Advisor ID.`  
`Dword - Unknown.`  
`Dword - Unknown.`  
  
`[start break]`  
`  Dword - Unknown.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  byte - Unknown.`  
`  Dword - Often has a specific (Advisor) Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - remaining at end of file after repeating section above.`

### Utilities CA2C2A2F

`Dword - File size of section.`  
`14 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name.`  
`String - Section Name (Advisor Name)`  
`Dword - Unknown.`  
`Dword - Unknown.`  
`Dword - Advisor ID.`  
`Dword - Unknown.`  
`Dword - Unknown.`  
  
`[start break]`  
`  Dword - Unknown.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  byte - Unknown.`  
`  Dword - Often has a specific (Advisor) Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - remaining at end of file after repeating section above.`

### Public Safety EA19E825

`Dword - File size of section.`  
`14 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name (The different advisor departments).`  
`Dword - Length of Section Name.`  
`String - Section Name (Advisor Name)`  
`Dword - Unknown.`  
`Dword - Unknown.`  
`Dword - Advisor ID.`  
`Dword - Unknown.`  
`Dword - Unknown.`  
  
`[start break]`  
`  Dword - Unknown.`  
`  Dword - Advisor Message Category/Group (Class ID).`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  Dword - Unknown.`  
`  byte - Unknown.`  
`  Dword - Often has a specific (Advisor) Message Reference (ID Value) here, otherwise it's usually 00000000.`  
`[end break]`  
`(And then repeats throughout file as per above, after the break.)`  
  
`Dword [00000000] - remaining at end of file after repeating sections above.`

### Environmental EAC937B4

`[start break ONE]`  
` Dword - File size of section.`  
` 14 Bytes - Unknown.`  
` Dword - Length of Section Name.`  
` String - Section Name (The different advisor departments).`  
` Dword - Length of Section Name.`  
` String - Section Name (Advisor Name)`  
` Dword - Unknown.`  
` Dword - Unknown.`  
` Dword - Advisor ID.`  
` Dword - Unknown.`  
` Dword - Unknown.`  
` [Start break TWO]`  
`   Dword - Unknown.`  
`   Dword - Advisor Message Category/Group (Class ID).`  
`   Dword - Unknown.`  
`   Dword - Unknown.`  
`   Dword - Unknown.`  
`   byte - Unknown.`  
`   Dword - May or may not have a specific (Advisor) Message ID Value here, mostly 00000000 though.`  
` [end break TWO]`  
` (And then repeats throughout section as per above.)`  
` `  
` Dword [00000000] - remaining at end of the section after repeating sections above.`  
`[end break ONE]`

And then repeat the WHOLE section above for repeating section (see below-Fluffy News).

### Fluffy News Advisor EAC937B4

This section is as per, and after, Environmental Advisor Section above.
