---
title: "Historical Graphs Subfiles"
description: ""
published: false
date: '2019-08-10T01:27:37Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:27:37Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Historical Graphs** file within [Savegame](/savegame) files. It is located at [TGI](/tgi) *89EFA536 299B2D1B 00000000*. This file contains historic and current data for a wide range of things. This specification is complete with the exception of two Header DWORDS (see Info 2).

## Specification

### File Header

    Dword - File length.
    Dword - Unknown1 (CRC or memory pointer)
    Dword - Unknown2 (CRC or memory pointer)
    Word - Version of Data Sets (always 2)
    Dword - Number of DataSourceID Sets

### Repeating Chunks

This section contains the actual data of the Historical Graphs. It is grouped based on data source types, defined by the [DataSourceID](/datasourceid).

    DataSourceID Header:

     Dword - Data Source ID. These are mostly found in the Graph/Trend Exemplars.
             There are other ones that exist though.
     Dword - Graph Type Flag (See Table 1)
     Dword - The number of Timing & Data pairs below. It's the number
             of Time/Data pairs that follow from here (for the given DataSourceID).

    Timing and Data pairs for a given DataSourceID:

     Dword - Date/Timing - Date that data is from (See Info 1)
     Dword - Data. This is the actual data, for the given Date/Timing
             for the given Data Source ID. More on this below.
     
     Repeat these pairs based on the Dword value above for the number of repeated pairs here.

Repeat 'Repeating Chunk' for Every [DataSourceID](/datasourceid) ID Value.

### Info 1: Date/Timing

Dates are stored in JD (Julian Dates) format (thanks [sawtooth](/people/sawtooth)). This format works differently than the standard date times in [EA](/ea) games and can be converted using the program here: <http://aa.usno.navy.mil/data/docs/JulianDate.html> or by likewise using our own conversion tools (we'd have to make one first obviously). Julian Dates start for [SimCity 4](/simcity-4) at 1/1/2000 which is the opening date for cities. This date format is also used by the in-game photo albums, see [INFO](/info). Also see the [Date Subfile](/date-subfile) for more information about this.

#### Table 1 - Graph/Type Flag

    Flag      Type        Data Timeframe    Graph Type
    --------------------------------------------------------------------------------------------
    00000000  Multiyear   Data Per Year     Line
    01000000  Single      Current Day       Single Value
    02000000  DoubleBar   Last two Months   Bar, i.e. Demand, etc. Only last value is displayed.
    0d160000  SingleYear  Daily for year    Line (may be others)    

### Info 2: Unknowns

Unknown1 and Unknown2 (in the file header) are similar to all other subfiles, and have in them some CRC information, and maybe a memory pointer, their purpose is to check if the subfile was corrupted while saving or loading.
