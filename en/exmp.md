---
title: "EXMP"
description: ""
published: true
date: '2019-08-09T02:54:54Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-03T02:50:13Z'
---

The following format is used by both [Exemplar](/exemplar) and [Cohort](/cohort) files in [SimCity 4](/simcity-4). A list of the properties within exemplars and cohorts can be found in the [exemplar properties](/exemplar-properties).

Exemplars/Cohorts can be either text or binary (text formats are found exclusively in Maxis plugins) and this can be determined by reading the fourth byte in any exemplar or cohort. In text files this is T and in binary files it is B. The following file specification is credited to [Buggi](/people/buggi), [Karybdis](/people/karybdis), [ILive](/people/ilive), and [Tropod](/people/tropod).

## Exemplar and Cohort File Format

        8 BYTES -   The file identifier. Can be EQZB1###, EQZT1### for exemplars and CQZB1### or CQZT1### for cohorts.
                    The fourth byte denotes whether the file is Text or Binary (T or B).
                    The fifth byte is the version number, which in these examples is 1.
        DWORD -     Parent cohort Type id
        DWORD -     Parent cohort Group id
        DWORD -     Parent cohort Instance id
        DWORD -     Property count. This specifies how many properties are
                    contained in the exemplar or cohort. Critical to reading the
                    file properly.
        +24         Repetitions of properties follow. Each property varies in size.
     
        
        Property structure
        ------------------
        All properties have the same basic structure. They start at offset 24 in an exemplar or cohort.

        DWORD -     The property's numerical value. Represented as 0x???????? in ILive's reader and DatGen4.
        WORD -      The property's '''ValueType'''. This defines weather its a uint or a float, etc.
                    See table below for possible values.
        WORD -      The property's '''KeyType'''. The KeyType contains a value of 0x80 if the property has more than or equal to one repetition,
                    and 0x00 if it has 0 repetitions. 0x80 is the only recorded KeyType

        (If KeyType is zero):
            BYTE -      Number of values, or value repetitions. (Seems to be always 0.)
            ARBIT -     A single value as defined by ValueType

        (If KeyType is 0x80):
            BYTE -      This is an unused flag.
            DWORD -     Number of values, or value repetitions. A repetition of 1 represents properties
                        capable of more than one repetition but held to 1 rep for the moment.
            ARBIT -     Value repetitions. Depending on data type, the length of these repetitions varies.
                        See ValueType below on data types.

## ValueType

        Type        Numeric value   Property values length
        ----        -------------   ----------------------
        SInt32      0x700           4
        Float32     0x900           4
        UInt32      0x300           4
        Bool        0xB00           1
        UInt8       0x100           1
        SInt64      0x800           8
        UInt16      0x200           2
        String      0xC00           Number of Reps Value is String Length
