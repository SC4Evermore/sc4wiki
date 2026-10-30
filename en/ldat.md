---
title: "LDAT"
description: ""
published: true
date: '2019-08-09T02:54:56Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-09-09T02:12:40Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**LDAT** or **LD** files are Lot Data files. They are sometimes packaged in with [Lot](/lot) files.

## Format

`4 bytes - Header/Version/Identifier`  
`4 bytes - Zone Compatibility`  
`4 bytes - Wealth Level`  
`4 bytes - Purpose`  
`4 bytes - Group`  
`4 bytes - Stage lot appears (contains values 1 - 8)`  
`2 bytes - Type (0001 - new lot, 0000 - replaces old lot)`  
`2 bytes - Lot width`  
`2 bytes - Lot depth`  
`2 bytes - Number of props in lot`  
`4 bytes - Number of dependencies in lot`  
`4 bytes - Length of Lot Name`  
`N bytes - Lot Name (length is set in previous four bytes)`  
  
`(Repeating chunk, repeats as many times as there are dependencies:)`  
`4 Bytes - Length of dependency name`  
`N Bytes - Dependency Name`

### Header Values

This value is always 1, as in Version 1.0.

### Zone Compatibility Values

Note: the values given below are decimal equivalents. For example, 128 (Resource) shows in [Reader](/reader) as 0x00008000.

`0     - Unknown`  
`1     - Undefined`  
`2     - Low Density`  
`4     - Medium Density`  
`8     - High Density`  
`12    - Medium Density`  
`14    - Low Density`  
`16    - Low Density`  
`32    - Medium Density`  
`64    - High Density`  
`96    - Medium Density`  
`112   - Low Density`  
`128   - Resource`  
`256   - Light`  
`512   - Heavy`  
`768   - Light`  
`896   - Light`  
`1024  - Military`  
`2048  - Airport`  
`4096  - Seaport`  
`8192  - Spaceport`  
`16384 - Landfill`  
`32768 - N/A`  
`38912 - Plopped`  
`64512 - Protected`

### Wealth Level Values

Note: the values given below are decimal equivalents.

`0 - N/A`  
`2 - $`  
`4 - $$`  
`8 - $$$`

### Purpose Values

Note: the values given below are decimal equivalents.

`0   - Ploppable`  
`2   - Residential`  
`4   - Commercial Service`  
`8   - Commercial Office`  
`16  - Unused `  
`32  - Industrial Agriculture`  
`64  - Industrial Processing`  
`128 - Industrial Manufacturing`  
`256 - Industrial High Tech`

### Group Values

Note: the values given below are decimal equivalents. For example, 5387 (Reward) shows in Reader as 0x0000150B.

`4096 - Residential`  
`4097 - Commercial`  
`4098 - Industrial`  
`4099 - Transportation`  
`4100 - Utility`  
`4101 - Civic`  
`4102 - Park`  
`4864 - Rail`  
`4865 - Bus`  
`4866 - Subway`  
`5120 - Power`  
`5121 - Water`  
`5376 - Police`  
`5377 - Jail`  
`5378 - Fire`  
`5379 - School`  
`5380 - College`  
`5381 - Library`  
`5382 - Museum`  
`5383 - Health`  
`5384 - Airport`  
`5385 - Seaport`  
`5386 - Landmark`  
`5387 - Reward`

### Type Values

`0 - Modified`  
`1 - Unique`
