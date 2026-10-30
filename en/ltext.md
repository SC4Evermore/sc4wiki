---
title: "LTEXT"
description: ""
published: true
date: '2025-01-07T14:14:51Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2008-07-27T10:31:19Z'
---

**LTEXT** or **Language Text** files are a Unicode text format used by [SimCity 4](/simcity-4) to give language specific text strings simply and quickly for use in any part of the world. Unicode of course makes this much easier since the vast number of characters can't always be written in standard text. LTEXT files cover everything from news to building and prop names to tool names in the game. They are queried by [Instance ID](/instance-id), so make sure your instance is unique when creating new ones!

LTEXT files are partially controlled by the [Delocalizers](/delocalizers) file, which gives the game instructions about converting text into the local language, or not.

LTEXT files are also related to the User Visible Name Key and Item Description Key in [exemplars](/exemplar). They can also contain HTML code that is used by the game. LTEXTs can also contain variables, to be filled in by the game with the appropriate value.

LTEXT files can be found in SimcityLocale.dat, as well as both Maxis and user-created plugin files. They are generally seen as an LTEXT or XA file by [Reader](/reader).

## Format Specification

### File Format

`WORD        Number of characters in the LTEXT.`  
`WORD        Text control character (see next)`  
`VALUE x n   Numeric value that corresponds to the Unicode code point`  
`            BYTE if control character is 0x0000`  
`            WORD if control character is 0x1000`

In English, decoding this is easy since non-compressed files will appear as an English character followed by a period (if the control character is 0x1000) in most hex editors. Other languages may be harder, i.e. Chinese, Korean. Compressed files do not have this same benefit.

## PHP Function

Here is a PHP function that returns the string enclosed in an LTEXT file:

    function ltextThing($data){
    /*ExemplarFile
        typeID: 6534284a
        $value = the 'content' array key*/

        $thing = str_split($data);
        foreach ($thing as $char => $word){
            if ($char % 2 == int and $char != 2)
                $return .= $word;
        }
    return $return; 
    }

## File Properties

### Tags

'Tags', enclosed with Hashes (#), can be included in an LTEXT file to mark where a writer wants dynamic content to be inserted into the text in-game. This can include the City Name or Monthly Costs, among other things.

| Tag | Content | Example Usage |
|----|----|----|
| \#m:<!-- unconverted template: var --># | The content of a linked Exemplar Property *as Currency* (200 is inserted as §200) | \#m:ea54d286# inserts the Monthly Cost of a building into the Item Description in a Menu Balloon |
| \#d:<!-- unconverted template: var --># | The content of a linked Exemplar Property *as it appears* (200 is inserted as 200) | \#d:27812852# inserts the Power Generation of a building into the Item Description in a Menu Balloon</br>\#d:4aa60ebc# inserts the Catalogue Capacity of a building into the Item Description in a Menu Balloon |
