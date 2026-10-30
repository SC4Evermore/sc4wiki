---
title: "Bridge RUL"
description: ""
published: true
date: '2019-08-09T02:55:12Z'
tags: ["File Formats/SC4", "Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2012-07-03T16:42:43Z'
---

**Bridge Specialization RULs** (often shortened to just "Bridge RULs") are special files that contain layout information for complex bridges such as arch bridges. They are not like the other [RUL](/rul) files, as their syntax is not [INI](/ini) based. All Bridge RULs have [Type ID](/type-id) *0x0A5BCF4B*, and [Group ID](/group-id) *0xAA5BCF57*, while the [Instance ID](/instance-id) for each varies as described below.

## History

The game originally only came with five Bridge RUL files, however others were possible and have been added over time. The original five files were for Roads, Rails, Elevated MHW, Avenue, and Ground MHW.

## Instances

The Bridge RULs have one Instance ID per network. They have the general format *0x0000100N* where *N* is the network ID.

List of Instance IDs:

- 0x00001000: Road
- 0x00001001: Rail
- 0x00001002: Elevated Maxis Highway
- 0x00001003: Street
- 0x00001004: Pipe *(Unused)*
- 0x00001005: PowerLine *(Unused)*
- 0x00001006: Avenue
- 0x00001007: Subway *(Unused)*
- 0x00001008: Light Rail
- 0x00001009: Monorail
- 0x0000100A: OneWayRoad
- 0x0000100B: Dirt Road/[RHW](/rhw)
- 0x0000100C: Ground Maxis Highway

Note that some networks currently do not have Bridge RUL files. The game does not require that a bridge RUL exists to draw bridges. Instead, any complex bridge will be drawn using simple rules dictated by the bridge exemplar.

## Game Mechanics

Once the game has decided that a network draw is suitable for bridge placement, the game picks a bridge (the first one that appears in the bridge selection menu) and evaluates it. The game knows the internal **Bridge ID** of the bridge (defined in the [Network INI](/network-ini)) and checks to see if a Bridge RUL for that network type exists. If the file exists, it looks inside of it to see if it has an entry for that Bridge ID. If one is found, then it evaluates the RUL within that file. The game looks for a layout line that has the same length as the bridge being drawn and produces the output. If the Bridge RUL, entry, or layout line with the proper length does not exist, the game evaluates the bridge using the exemplar and internal layout system.

## Format

The format of Bridge RULs differ greatly from the other RULs as they are not INI based. Instead, bridge RULs use start declarations and *end* tags. Comment lines begin with the \# symbol.

Bridge RUL files consist of individual sections for each bridge listed within. Each bridge section then contains a header, repeating section definitions, repeating layout definitions, and finally and *end* flag. The general format of the file looks like:

    bridge ID (header)
      section definition 1
      section definition 2
      ...
      section definition n
      layout definition 1
      layout definition 2
      ...
      layout definition n
    end

    (repeat)

### Header

Each bridge section begins with a header, which is simply one line containing the Bridge ID for that bridge. The ID is the same one in the Network INI.

    bridge ID

### Section Definitions

Section Definitions define a named segment (`SECTIONNAME`) of the bridge, consisting of one or more piece lines. These sections can then be called by name in other Section Definitions and the Layout Definitions to avoid having to list each tile individually for each line. They may consist of only a single piece line, or several.

    section SECTIONNAME
       piece <IID, ROTATION>
       ...
    end

Piece lines have 4 varieties:

1.  **Simple piece**:
        piece <IID, rotation>
2.  **Sloped piece**:
        piece <IID, rotation, deltaHeight, yOffset>

    *deltaHeight* is the change in height across the tile (along the network) and *yOffset* is how far the model should be offset vertically.
3.  **Column piece**: Consists of either a Simple or Sloped piece followed by a Depth callout:
        <IID,...>:Depth

    *Depth* defines how far down the support column goes.
4.  **Compound piece**: Consists of several other section definitions strung together:
        SectionName_1 SectionName_2 ... SectionName_n

    This will import all of the pieces defined in each of the sections being called. The same modifiers used on Layout Definitions also work here.

When a section contains multiple piece lines, the evaluation depends on the tile width of the network. For single-tile-wide networks, each line simply adds another tile to the length of the section. For dual-tile networks, every two lines adds another tile to the length of the section (every two lines make up the two tiles that make up a two-tile-wide bridge).

Many sections are often defined to consolidate sections of a bridge such as having a section for the end piece, the approach, the support, start of the arch, middle of the arch, end of the arch, etc. Sections should be named using a short but descriptive name (although many [NAM](/nam) and Maxis items use rather cryptic names). Uppercase letters don't seem to be allowed, but numbers are.

### Layout Definitions

The final part of the bridge definition is the Layout Definitions. These are used to define the piece layout for bridges of specific lengths by specifying a string of Bridge Sections. Any bridge length not defined here is handled by the Bridge Exemplar.

Note that these sections may have two different formats:

    length LEN
       piece SectionName_1 SectionName_2 ... SectionName_n
    end

Or

    length LEN
       piece SectionName_1
       piece SectionName_2
       ...
       piece SectionName_n
    end

*LEN* tells the game what length of bridge this section applies to. Note that this counter starts at zero, so acceptable values for *LEN* go up to 255. Note also that since bridges cannot cross city boundaries, it is not necessary to define bridges longer than 256 tiles since they cannot be built. However, bridges lengths up to 256 tiles may be, and often are, defined in these files.

*SectionName_x* is the name of various sections defined previously in the file, in the Section Definitions for this bridge type.

The *SectionNames* may be modified in various ways to shorten the necessary definition:

- Prefixing a *SectionName* with a number and an asterisk (\*) will repeat that section that number of times (i.e., `3*endpiece` will repeat `endpiece` 3 times).
- Using `rev(SectionName)` will reverse the section.
