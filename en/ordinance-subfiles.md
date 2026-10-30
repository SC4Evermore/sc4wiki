---
title: "Ordinance Subfiles"
description: ""
published: true
date: '2024-12-18T09:45:53Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:22:55Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This page pertains to the format of the **Ordinances** file within [Savegame](/savegame) files.

More information about the game's Ordinances can be found in the [Ordinance](/ordinance) article.

## Specification

This specification covers the format of all ordinance files within [SimCity 4](/simcity-4) Savegame files. The relevant [Type IDs](/type-id) are as follows: *00D0723D, 02BF1DFA, 22F6E80C, 22F6E81B, 40D07236, 42BF1E18, 62BF1DAA, 62BF1DB9, 62F6E7CF, 815B4CEF, 82B9999B, A0D07129, A2BF1DDC, A2BF1DE5, A2BF1E43, C2BF1DC5, C2BF1E04, C2F6E81F, E0D0722E, E0D07233*.

    Dword   - File size
    Dword   - CRC checksum
    Dword   - Memory address
    Word    - Version, always 4.
    Byte    - Initialized (Tracks if the ordinance class initialization method has been called).
    Dword   - Type ID of file/Ordinance ID.
    Dword   - Length of Ordinance Name.
    String  - Ordinance Name.
    Dword   - Length of Ordinance Description.
    String  - Ordinance Description.
    Dword   - Year available.
    Dword   - Prior to City Incorporation, this is Monthly Chance. After incorporation, it changes.
    Qword   - Enactment Income.
    Qword   - Retractment Income.
    Qword   - Monthly Constant Income/Expense.
    Float32 - Monthly Income factor. 
    Dword   - Advisor ID (unused, always 0)
    Byte    - Available to Enact (In other words, is it actually showing up in the Ordinance screen or not).
    Byte    - Ordinance On/Off (That is, whether the Ordinance has actually been enacted or not by the user).
    Byte    - Enabled (Can the ordinance show up in the menu or be turned on).
    Byte/QWord - Dual purpose:
                 For Byte - City nonincorporated it's always 01.
                 For QWord - Current Monthly Income/Expense.
                 Once a city becomes incorporated it becomes a Qword for Monthly Income/Expense.

    Byte    - Ordinance Category; Income/Expense.

    Ordinance Property Data:

    Word    - Exemplar Property Data Version (always 2).
    Word    - Generic Property Data Version (always 2).
    Dword   - Generic Property Count (always 0).
    Dword   - Group ID of Ordinance Exemplar.
    Dword   - Type ID of Ordinance Exemplar.
    Dword   - Instance ID of Ordinance Exemplar and/or Ordinance ID.
              (Seems to also be the same as the Type ID of the ordinance file in the savegame).
