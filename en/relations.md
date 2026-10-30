---
title: "Relations"
description: ""
published: false
date: '2019-08-04T05:40:34Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-08-06T03:50:26Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

This article contains a list of all the relations of the [SimCity 4](/simcity-4) [file types](/list-of-file-formats) as currently known. This will exclude the [Savegame](/savegame) formats as their parents are the .exe, and their children are any number of files that it decides to pull in as it wants to: building exemplars for the building file and so forth. This article shows the parents of each file, namely, the file which is responsible for the file type opening, and the children, which are things it causes to open.

## Entry Format

**File Type**

<GID>` - `<Group Name>  
`        0xAAAABBBB (optional) - For Group IDs with multiple section types, the format for that group type  `  
`        Children - Things loaded as a result of this file.`  
`           Relations (name, kind, property ID if available)`  
`        Parent - Things that caused this file to be loaded`  
`           Relations (name, kind, property ID if available)`  
`        Dependent - (optional) - Dependent relations. A file contains details that are carried out by another file`  
`           Relations (name, kind, property ID if available)`

To show different variations of Instances inside a [Group ID](/group-id) that may have different children and parents, instance format codes like used in the [InstanceFormats](/instanceformats) spec may be seen in the usual 0xAAAABBBB type format.

The 'kind' part of a relation may be dropped if the file is being called by the .exe in order for a full description. No Relations of either parent or child type are marked by a NONE designation. Filetypes for which all relations are not marked are listed at the end of the document.

This document may not be complete. Things may be assumed to be complete until shown otherwise, for which corrections would then be made to whatever part is missing data.

## Specification

### A - D

**AB**

`8a5971c5 - UDI Sounds`  
`           Children`  
`           Parent`  
`              Vehicle Exemplar, Exemplar Prop, 0xAC08657C`

**AE**

`8a5971c5 - UDI Data`  
`           Children`  
`           Parent`

**ATC**

`2a2458f9 - Props Animation Collections`  
`           Children`  
`              AVP, One AVP per designated IID `  
`           Parent`  
`              Lot Configs, Property, Value 13+ for Type 0x1 lines`  
`              Exemplars, Resource Key, 0xC96E6806 group exemplars may call these animations.`  
`49a593e7 - Non-prop Animation Collections`  
`           Children`  
`              AVP, One AVP per designated IID `  
`           Parent`  
`              EXE, Automata Placement Routine`  
`              Exemplars, Resource Key, 0xC96E6806 group exemplars may call these animations.`

**AVP**

`2a2458f9 - Props Single Animation `  
`           Children`  
`              FSH, Instance ID, FSH has same instance as AVP. Plane of FSH is in each frame`  
`           Parent`  
`              ATC, Resource Key, One AVP per Zoom as listed in ATC`  
`49a593e7 - Non-Prop Single Animation`  
`           Children`  
`              FSH, Instance ID, FSH has same instance as AVP. Plane of FSH is in each frame`  
`           Parent`  
`              ATC, Resource Key, One AVP per Zoom as listed in ATC`

**BMP**

`6A1EED2C - Region tile layout bitmaps`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, these bitmaps represent default Maxis region layouts and are called as needed.`  
`1d6962cf - SC4 Vanilla Internal Tool Bitmaps`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Called when using Maxis Tools in an uncompiled version programming mode.`  
<gen>` - Computer specific BAT generated overlay picture (small)`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Created and used by the Building tool suite to create in-game representative images.`

**BSPEC**

`aa5bcf57 - Bridge Specification Rules`  
`           Children`  
`              Exemplar, piece, Bridge specifications define pieces of the bridge`  
`                        by linking to its applicable Exemplar through the piece.`  
`           Parent`  
`              EXE, Instance, The EXE calls the BSPEC directly by instance,`  
`                   and then reads optional bridges by # name inside it.`

**Cohort**

`07BDDF1C - Civic and Park Building Parents`  
`           0xABBBBCCC (Automata Layer Cohorts)`  
`              Children`  
`              Parent`  
`           0x0000000A (Main Usage Cohorts)`  
`              Children`  
`              Parent`  
`096E6739 - Vehicle Type Parents`  
`           0x0000000A (Main Vehicle Cohorts)`  
`              Children`  
`              Parent`  
`           0xABBBBCCC (Automata Layer Cohorts)`  
`              Children`  
`              Parent`  
`096e6817 - Watercraft Parents`  
`           Children`  
`           Parent`  
`296e680f - Aircraft Parents`  
`           Children`  
`           Parent`  
`47bddf12 - Zonable Commercial Building Parents`  
`           Children`  
`           Parent`  
`67bddf0c - Zonable Residential Building Parents`  
`           Children`  
`           Parent`  
`690f693f - Dataview Parents`  
`           Children`  
`           Parent`  
`6a297266 - MySim Parent`  
`           Children`  
`           Parent`  
`7a4a8458 - Clouds Parent`  
`           Children`  
`           Parent`  
`a7bddf17 - Zonable Industrial Building Parents`  
`           Children`  
`           Parent`  
`a8fbd372 - Building Foundations`  
`           Children`  
`           Parent`  
`c96e6806 - Crime Simulator`  
`           0x0000000A (Main Sim Effectors)`  
`              Children`  
`              Parent`  
`           0xABBBBCCC (Sim Cohorts)`  
`              Children`  
`              Parent`  
`ca25875d - Ambiance Layer`  
`           Children`  
`           Parent`  
`ca386e22 - Landmark Parent`  
`           Children`  
`           Parent`

**Config (CFG)**

`49dd6e08 - SimCity Configuration File`  
`           Children`  
`              Region, Entry, Tells the EXE the currently loaded region and location`  
`           Parent`  
`              EXE, called on load.`

**Cursor**

`00000001 - Black & White Cursors`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, call, Called directly as needed in game dependent on colour quality.`  
`00000004 - 4bit Cursors`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, call, Called directly as needed in game dependent on colour quality.`  
`00000008 - 8bit Cursors`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, call, Called directly as needed in game dependent on colour quality.`  
`00000032 - 32bit Cursors`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, call, Called directly as needed in game dependent on colour quality.`

**DBPF**

`6a5b7b57 - DBPF Data files`  
`           Children`  
`              NONE`  
`           Parent`  
`              LUA, tutorial_file_guids[#], defines an IID for a DBPF file for use in`  
`              that tutorial where # is the tutorial number as set.`

**DIR**

`e86b1eef - Compressed File Directory`  
`           Children`  
`              NONE, However has a list of all Compressed files in the dat.`  
`           Parent`  
`              DBPF Files (external), Load, File loaded at DBPF load to expedite processing.`

### E - K

**Effect Dir**

`ea5118b1 - Effect Resource Tree`  
`           Children`  
`              FSH, ResourceKey, In section 1 the effect may call itself a texture by instance.`  
`              S3D, ResourceKeys, In section 1 a list of resource keys may call random S3D files.`  
`              FSH, Resourcekey, In Section 2 terrain dependent FSH file.`  
`              Exemplar, ResourceKey, In section 5 terrain brush exemplar.`  
`              LUA, String, Section 6 string links to a representative string in LUA generators/attractors/repulsors by var.`  
`              EXE, CID, Section 7 U4 property almost certainly links to the exe by classid.`  
`              TRK, ResourceKey, Section 9 resource Key links to a track def for sounds.`  
`              EXE, String, Section 10 strings almost certainly link to the EXE for train variables.`  
`              EXE, CID, U4 in section 12 probably links to the exe by classid.`  
`           Parent`  
`              EXE, CID, the exe may call an effect in 13,14,15 by instance or CID.`  
`              EXE, String, the exe may call a string in the effdir directories 13,14,15 by name.`  
`              Exemplar, property, 0x4a08c700 property calls an effect name for use by exemplars (often disasters).`  
`              Exemplar, property, 0xc98204b8 property calls an effect name for use in an effect exemplar by string.`  
`              Exemplar, property, 0xc98204b9 property calls an effect name for use in an effect exemplar by string.`  
`              Exemplar, property, in absence of the 0xc98204b8/9 property Exemplar name of gid 0xc977c536 calls an effect by string.`  
`              S3D, name, the effect name in the REGP section of an S3D may spawn an effect by directory name in the EFFDIR.`  
`              LUA, , fx, the fx command allows to reference an effect inside the effect dir from an LUA.`

**Exemplar**

`07BDDF1C - Exemplar - Civic and Park Buildings`  
`           0xAAAABBBB - Civic`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Park`  
`              Children`  
`              Parent`  
`084344E0 - Exemplar - Network Placement Tuning Parameters`  
`           Children`  
`           Parent`  
`088E1962 - Exemplar - Power Poles`  
`           Children`  
`           Parent`  
`096E6739 - Exemplar - Land Vehicle Types`  
`           0xAAAABBBB - Vehicles`  
`              Children`  
`              Parent`  
`           0xABBBBCCC (rarely used. backup format)`  
`              Children`  
`              Parent`  
`096E6817 - Exemplar - Water Vehicle Types`  
`           0xAAAABBBB - Vehicle`  
`              Children`  
`              Parent`  
`           0xABBBBCCC (rarely used. backup format)`  
`              Children`  
`              Parent`  
`2821ED93 - Exemplar - Bridge Pieces Network Part Assignment`  
`           0xAAAABBBB - Bridges, and Lightmaps`  
`              Children`  
`              Parent`  
`296E680F - Exemplar - Air Vehicle Types`  
`           0xAAAABBBB - Vehicles`  
`              Children`  
`              Parent`  
`           0xAAAAAAAA (test exemplar)`  
`              Children`  
`              Parent`  
`2989FD57 - Construction Properties`  
`           Children`  
`           Parent`  
`29B6C670 - Exemplar - Disasters`  
`           0x0000000A - Disasters`  
`              Children`  
`              Parent`  
`           0xABBBBCCC (Rush Hour Disasters)`  
`              Children`  
`              Parent`  
`2A3858E4 - Exemplar - Menu Items`  
`           0x00000AAA`  
`              Children`  
`              Parent`  
`           0xAAAABBBB (Intersections)`  
`              Children`  
`              Parent`  
`2B79DFFB - Exemplar - Light Rail Pieces`  
`           0xAAAAAAAA (test exemplar format)`  
`              Children`  
`              Parent`  
`           0xAABBCCDE - 3d Networks`  
`              Children`  
`              Parent`  
`47BDDF12 - Developer: Commercial`  
`           Children`  
`           Parent`  
`67BDDF0C - Developer: Residential`  
`           Children`  
`           Parent`  
`67CD5FA1 - Exemplar - Building Behavior Simulators`  
`           0xABBBBCCC (rarely used. backup format)`  
`              Children`  
`              Parent`  
`           0x0000AABB - Building Behavior`  
`              Children`  
`              Parent`  
`690F693F - Exemplar - Data view and U-Drive-It Interfaces`  
`           Children`  
`           Parent`  
`6A01FC2A - Exemplar - God Mode Terrain Tools`  
`           Children`  
`           Parent`  
`6A297266 - Exemplar - MySims`  
`           Children`  
`           Parent`  
`7A4A8458 - Exemplar - Tuning Parameters/Background Loaders`  
`           Children`  
`           Parent`  
`88CD66E9 - Exemplar - Fluid Dynamics Properties`  
`           Children`  
`           Parent`  
`8974F80F - Exemplar - Supports`  
`           Children`  
`           Parent`  
`89AC5643 - Exemplar - Transit Pieces (minus light rail)`  
`           Children`  
`           Parent`  
`89C2A517 - Exemplar - Textures`  
`           Children`  
`           Parent`  
`8A3858D8 - Exemplar - Rewards`  
`           Children`  
`           Parent`  
`A7BDDF17 - Developer: Industrial`  
`           0xAAAABBBB - Buildings`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Fields`  
`              Children`  
`              Parent`  
`A82CA30F - Exemplar - Bridge Pieces Main Definition`  
`           Children`  
`           Parent`  
`A8434037 - Exemplar - Highway Pieces Definitions`  
`           Children`  
`           Parent`  
`A8FBD372 - Exemplar - Building Lots`  
`           0xAAAABBBB - Lots`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Lots Format2`  
`              Children`  
`              Parent`  
`A9189CF0 - Lighting Exemplar`  
`           Children`  
`           Parent`  
`A998D30B - Automata Tuning Exemplar`  
`           Children`  
`           Parent`  
`A9C2C209 - Exemplar - Ordinances`  
`           Children`  
`           Parent`  
`C7BB4816 - Exemplar - Demand Simulator`  
`           Children`  
`           Parent`  
`C8DBCCBA - Exemplar - Utility Buildings`  
`           Children`  
`           Parent`  
`C96E6806 - Exemplar - Animated Props`  
`           0xAABB0000 - Props`  
`              Children`  
`              Parent`  
`           0xAAABBB00 - Non-Settable Props`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Sims`  
`              Children`  
`              Parent`  
`C977C536 - Exemplar - Props`  
`           0xAAAABCCC - LODs and Effects`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Props`  
`              Children`  
`              Parent`  
`CA25875D - Exemplar - Ambiance Layer Functionality`  
`           Children`  
`           Parent`  
`CA386E22 - Exemplar - Landmarks`  
`           Children`  
`           Parent`  
`CA4AD545 - Exemplar - Graphs`  
`           Children`  
`           Parent`  
`CB730FAC - Exemplar - Avenue Bridge Pieces Resources`  
`           Children`  
`           Parent`  
`CBE084CB - Exemplar - One way Network Intersections & Road Tunnel`  
`           Children`  
`           Parent`  
`E7E2C2DB - Exemplar - Simulators`  
`           Children`  
`           Parent`  
`E8347989 - Exemplar - Rail & Highway Bridge Pieces Resources & Rail Tunnel`  
`           Children`  
`           Parent`  
`E83E0437 - Exemplar - Trees`  
`           Children`  
`           Parent`  
`EA12F32C - Exemplar - Crimes`  
`           Children`  
`           Parent`  
`EBE084C2 - Exemplar - 3D Transportation Pieces - Monorail/Light Rail`  
`           Children`  
`           Parent`  
`EBE084d1 - Exemplar - 3D Transportation Pieces - Ground Highway`  
`           Children`  
`           Parent`  
<gen>`  - Computer specific Plugin Manager generated Group ID (same as lots)`  
`           Children`  
`           Parent`

**FSH**

`0986135E - FSH - Base and Overlay Textures`  
`           Children`  
`           Parent`  
`1ABE787D - FSH - Building Textures/Bridge Textures/Misc Textures/Network Textures`  
`           0xAABBCCDE - Network Textures`  
`              Children`  
`              Parent`  
`           0xAAAABCDE - LODs (Buildings, Props etc.)`  
`              Children`  
`              Parent`  
`           0xAAAABCD0 - Flora`  
`              Children`  
`              Parent`  
`          0xAAAA000B - Graffiti (1dc##### in SimCity_2.dat)`  
`              Children`  
`              Parent`  
`          0xABBBBCCC - Sim & Automata & Fauna & Masks & Clouds`  
`              Children`  
`              Parent`  
`          0xAAAAB00C - Construction & Materials Textures`  
`              Children`  
`              Parent`  
`2A2458F9 - FSH - Animation Sprites for Props`  
`           Children`  
`           Parent`  
`2BC2759A - FSH - Transit Piece Masks`  
`           Children`  
`           Parent`  
`49A593E7 - FSH - Animation Sprites non Props`  
`           Children`  
`           Parent`  
`891B0E1A - FSH - Terrain & Foundation Textures/Masks/Effect Textures`  
`           0x0000AAAA - Terrain`  
`              Children`  
`              Parent`  
`           0xABBBBCCC - Masks & Effects`  
`              Children`  
`              Parent`  
`           0xAAAA000B - Foundations`  
`              Children`  
`              Parent`  
`cb6b7bd9 - LE Arrow Images`  
`           Children`  
`           Parent`  
`46A006B0 - FSH - User Interface Images`  
`           Children`  
`           Parent`  
<gen>` - Computer specific BAT generated Texture groupid`  
`           Children`  
`           Parent`

**HIT**

`ca4d19e3 - HIT Audio Track Data`  
`           Children`  
`           Parent`  
`              INI, Resource, In the sound INI file [trackdatablocks] area each HIT file is defined.`

**HLS**

`9dbdbf74 - Sound Hitlists`  
`           Children`  
`              TRK, IID, TRKs can be referenced if needed by IID.`  
`              XA, IID, XAs of any type can be referenced in this way by IID.`  
`              WAV, IID, Custom WAVs instead of XA can be referenced in this way.`  
`           Parent`  
`              TRK, Field, Field 15 of TRK files where entered.`

**INFO**

`xxxxxxxx - Photo Album Information File (does not have TGI)`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Called as the UI for the Album needs it.`

**INI**

`4a87bfe8 - Font INI`  
`           Children`  
`              MXF, name, calls to font.mxf files done by the first assigned property of each font assignment line.`  
`           Parent`  
`              EXE, instance, direct call to the font ini file by the exe`  
`              UI, property, any font property may make a direct call to one of the font lines in this INI.`  
`8a5971c5 - Terrain Mapping, Sound, and Features INI`  
`           Children`  
`              HIT, Resource, In the sound INI file [trackdatablocks] area each HIT file is defined.`  
`              FSH, Instance key, Partial instances are presented in the terrain.ini that`  
`                   link to FSH textures in table form via moisture level.`  
`              EXE, CIDs, In the sound INI file classids for the exe are defined for various sound bits.`  
`           Parent`  
`              EXE, Instance, Direct call to sound ini as needed by instance.`  
`              EXE, Instance, direct call to the terrain ini as needed by the exe.`

**JFIF/JPEG**

`ca133ecb - JPEG Art`  
`           Children`  
`              NONE`  
`           Parent`  
`              UI, image, called as a resource key by the image property during design phases,`  
`                  this represented placeholders.`  
<gen>` - Computer specific BAT generated overlay picture (large)`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Created and used by the Building tool suite to create in-game representative images.`

**KEYCFG**

`6a231eaa - Accelerator Tables`  
`           Children`  
`              Exemplar, IID, Extra data in the keyconfigs links to lot exemplars.`  
`           Parent`  
`              EXE, loaded at start.`

### L - R

**LEV and XA**

XAs currently in the LEV area.

`0a5bcda5 - Construction`  
`           Children`  
`              XA, GroupID, XA files inside this Groupid linked to parent LEV.`  
`           Parent`  
`              Exemplar, Property, 0xEA3FBDD7 - Audio:FreshScoreKey`  
  
`The following Group ID's have the same Parent/Child info as above:`  
`0a627909 - Residential Bad Night Small/Medium`  
`2a398e45 - Nature Night`  
`2a6278ee - Residential Bad Day Large`  
`4a392cff - Industrial Clean Bad`  
`4a398e40 - Nature Day`  
`4a42c073 - Traffic Midtown/Medium`  
`4a54e37f - Pipe View`  
`4a54e387 - Subway View`  
`4a5e6ac5 - High Crime`  
`4a5e7be3 - Farm Buildings`  
`4a60ce67 - Farm Fields`  
`4a627900 - Residential Bad Night Large`  
`8a398e3c - Industrial Dirty Good`  
`8a42b774 - Traffic Downtown`  
`8a60ce80 - Traffic Street`  
`8a60cf62 - Zoo`  
`8a627912 - Residential Good Day Small/Medium $$$`  
`aa39ba06 - Garbage`  
`aa60ce7d - Traffic Road Light`  
`ca398e36 - Industrial Dirty Bad`  
`ca398e4a - Wind Zoom 1&2`  
`ca62790f - Residential Good Day Small/Medium`  
`ca88cc85 - Abandoned`  
`ea39ba3e - Water`  
`ea5e6ac2 - Traffic Jam`  
`ea60ce77 - Traffic Highway`  
`ea6278fd - Residential Bad Day Small/Medium`  
`ea62790c - Residential Good Day`  
`ea627915 - Residential Good Night Small/Medium`  
`ea627918 - Zoom 3 City`  
`ea62791b - Wind Zoom 3`  
`ea398e29 - Industrial Clean Good`

**LogicObject (TLO)**

`ca4d19e3 - Track Logic Object`  
`           Children`  
`              Effect dir, effect string, Strings of effects where present.`  
`           Parent`  
`              TRK, Field, Field 4 of TRK files where applicable.`

**Lot Data (LD)**

`6be74c60 - Exchange Data for Lot`  
`           Children`  
`              NONE, however lists required plugin dats to use this Lot in-game. Not actual link. Just theoretical.`  
`           Parent`  
`              Exchange, Upload Function, Processed during upload to display information.`

**LTEXT**

LTEXT files in Plugins have incremental GIDs to signify the different languages to the exe.

`EA5524EB - LTEXT - Misc. Item Names/Descriptions`  
`           Children`  
`           Parent`  
`EA231E96 - LTEXT - Misc. Texts`  
`           Children`  
`           Parent`  
`CA554B03 - LTEXT - Popup window HTML texts`  
`           Children`  
`           Parent`  
`8A635D24 - LTEXT - Audio filename to description texts`  
`           Children`  
`           Parent`  
`8A5E03EC - LTEXT - Disaster texts`  
`           Children`  
`           Parent`  
`8A4924F3 - LTEXT - About SC4 window HTML text`  
`           Children`  
`           Parent`  
`6A554AFD - LTEXT - Misc. Item Names/Descriptions`  
`           Children`  
`           Parent`  
`6A3FF01C - LTEXT - Game UI Texts`  
`           Children`  
`           Parent`  
`6A231EAA - LTEXT - Interactivity Feature Texts (MySim, UDriveIt, etc.)`  
`           Children`  
`           Parent`  
`6A231EA4 - LTEXT - News ticker message texts`  
`           Children`  
`           Parent`  
`4A5E093C - LTEXT - Terrain tool texts`  
`           Children`  
`           Parent`  
`4A5CB171 - LTEXT - Funny random city loading message texts`  
`           Children`  
`           Parent`  
`2A592FD1 - LTEXT - Item plop/draw notification texts`  
`           Children`  
`           Parent`  
`0A554AF5 - LTEXT - Audio UI Panel texts`  
`           Children`  
`           Parent`  
`0A554AE8 - LTEXT - General UI texts`  
`           Children`  
`           Parent`  
`0A554AE0 - LTEXT - Item visible name and description texts`  
`           Children`  
`           Parent`  
`0A419226 - LTEXT - In game error texts`  
`           Children`  
`           Parent`  
`6a4eb3f7 - LTEXT - Population Text`  
`           Children`  
`           Parent`  
`EAFCB180 - LTEXT - Plugin Install Text`  
`           Children`  
`           Parent`

**De-Localizer**

The Delocalizer is located in the LTEXT files.

`6a231eaa - Text to avoid language localization.`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Loaded when the EXE processes files containing LTEXTs.`

**LUA**

`4A5E8EF6 - LUA - Missions, Advisors, Advice, Definitions, Tutorials and Packaging files`  
`           Children`  
`              LUA, dofile, Dofile commands load a file by hashed name translated to instance.`  
`              LTEXT, Resource Key, text@0x######## tutorial functions define an instance for a GID 0xca554b03 LTEXT.`  
`              LTEXT, Resource Key, text@0x######## mission/advice functions define an instance for a GID 0x6a231ea4 LTEXT.`  
`              DBPF, tutorial_file_guids[#], defines an IID for a DBPF file for use`  
`                    in that tutorial where # is the tutorial number as set.`  
`              S3D, Advisor_anim_types, this variable defines the IID of an S3D file for various types of animations.`  
`              PNG, sit_constants, PNGs as defined by mission constants by IID.`  
`              Exemplar, ordinance_ids, ordinance ID defines an IID of an ordinance Exemplar.`  
`              LUA, function, functions can be used to indirectly call a LUA and connect them.`  
`              Exemplar, flora_tool_types, this calls the IID of an model exemplar.`  
`              Exemplar, building_group_types, this calls the IID of an model exemplar.`  
`              Exemplar, graph_window_types, this calls the IID of a Group 0xca4ad545 exemplar.`  
`              Exemplar, tuning_constants, this calls the IID of an model exemplar.`  
`              Exemplar, special_buildings, this calls the IID of an model exemplar.`  
`              BMP, Mysim_balloons, This calls a MySim balloon IID of the 0xab7e5421f Group ID.`  
`              TRK, mysim_vox, This calls a MySim TRK IID of the 0xca4d1948 Group ID.`  
`           Parent`  
`              LUA, dofile, Dofile commands load a file by hashed name translated to instance.`  
`              Itself, ID, At start of file, "--#-package:01234567# -- package signature",`  
`                      the package ID must be unique for all LUA.`  
`              Itself, rawget, line in following format:`  
`                      [if not rawget(globals(), "_unique_name_here") then _unique_name_here = 1]`  
`              LUA, function, functions can be used to indirectly call a LUA and connect them`  
`              EXE, As needed can call directly`  
`           Dependent`  
`              LUA, function, A function declared and created in one LUA can be run from another LUA to reference and call.`  
`              LUA, reward_state, reward states as defined in the main def file and referenced by other LUAs.`  
`              LUA, building_conditions, building conditions as defined in the main def file and referenced by other LUAs.`  
`              LUA, zone_tool_types, tool types for zones as defined in the main def file and referenced by other LUAs.`  
`              LUA, game_trends, game trends as defined in the main def file and referenced by other LUAs.`  
`              LUA, zodiac, mysim zodiacs as defined in the main def file and referenced by other LUAs.`  
`              LUA, mysim_trip_types, mysim trip types as defined in the main def file and referenced by other LUAs.`  
`              LUA, game_difficulty_level, difficulties as defined in the main def file and referenced by other LUAs.`  
`              LUA, mysim_idle_animation_ids, animation ids for mysims as defined in the main def file and referenced by other LUAs.`  
`              LUA, advice_priority, advice text priority as defined in the main def file and referenced by other LUAs.`  
`              LUA, camera_zooms, camera zooms as defined in the main def file and referenced by other LUAs.`  
`              LUA, ordinance_ids, ordinance ids as defined in the main def file and referenced by other LUAs.`  
`              LUA, neighbor_deal_types, neighbour deal types as defined in the main def file and referenced by other LUAs.`  
`              LUA, disaster_ids, disaster ids as defined in the main def file and referenced by other LUAs.`  
`              LUA, game_events, game events container and types  as defined in the main def file and referenced by other LUAs.`  
`              LUA, game_commands, game commands as defined in the main def file and referenced by other LUAs.`  
`              LUA, network_types, network types as defined in the main def file and referenced by other LUAs.`  
`              LUA, button_tool_types, tool types for buttons  as defined in the main def file and referenced by other LUAs.`  
`              LUA, flora_tool_types, flora tool types  as defined in the main def file and referenced by other LUAs.`  
`              LUA, effects, effects  as defined in the main def file and referenced by other LUAs.`  
`              LUA, building_group_types, building group types  as defined in the main def file and referenced by other LUAs.`  
`              LUA, budget_window_types, budget window types as defined in the main def file and referenced by other LUAs.`  
`              LUA, graph_window_types, graph window types as defined in the main def file and referenced by other LUAs.`  
`              LUA, map_window_types, map window types as defined in the main def file and referenced by other LUAs.`  
`              LUA, tuning_constants, ones which are not just a constant  as defined in the main def file and referenced by other LUAs.`  
`              LUA, special_buildings, special buildings  as defined in the main def file and referenced by other LUAs.`  
`              LUA, mysim_balloons, mysim thought balloons as defined in the main def file and referenced by other LUAs.`  
`              LUA, mysim_vox, mysim audio as defined in the main def file and referenced by other LUAs.`  
`              LUA, game_commands, game commands as defined in the main def file and referenced by other LUAs.`  
`              LUA, building_groups, building groups for missions as defined in the constant LUA file.`  
`              LUA, sit_conditions, mission conditions as defined in the constant LUA file.`  
`              LUA, sit_constants, constants for missions as defined in the constant LUA file.`  
`              LUA, tutorial_zone_type, zone types as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, tutorial_building_type, building types as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, tutorial_dispatch_type, dispatch types as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, tutorial_network_type, network types as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, tutorial_buttons, buttons as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, tutorial_function_index, functions as defined in the main tutorial file and referenced by other LUAs.`  
`              LUA, automata_groups, automata groups as defined in the constants LUA.`  
`              LUA, automata_states, automata states as defined in the constants LUA.`  
`              LUA, sit_coverage_state, coverage states as defined in the constants LUA.`  
`              LUA,tuning, tuning constant variables link to definitions in another LUA.`  
`              LUA, #link#, a #function# resource type loads that resource from a defining LUA.`  
`              LUA, advice_mood, advice moods are stored in another LUA file and accessed from other LUAs.`  
`              LUA, Advice_type, defined in LUA based off of Advisor IDs from the exe and accessed from LUA.`  
`              LUA, automata, An LUA may declare an automata group from another file be affected by it.`  
`              LUA, add_tutorial and task_first, These lines define a GUID which links the tutorial def fine to the actual tutorial.`  
`              EXE, part of the EXE may be called by a classid/guid definition.`  
`              EXE/LUA, MySim, MySim variables incoming from the game are defined in LUA and accessed from elsewhere.`  
`              EXE/LUA, game, game variables are stored in the LUA and modified but essentially come direct from the EXE.`  
`              EXE, Advisor_id, this variable is defined elsewhere and accessed from Advisor LUA script.`  
`              EXE, tutorial_zone_type, defined in the EXE and subaccessed from LUA.`  
`              EXE, tutorial_network_type, network types as defined in C++ and sent to LUA.`  
`              EXE, tutorial_dispatch_type, dispatch types as defined in C++ and sent to LUA.`  
`              EXE, tutorial_zone_type, zone types as defined in C++ and sent to LUA.`  
`              EXE, tutorial_buttons, tutorial buttons as defined in C++ by classid and sent to LUA.`  
`              EXE, tutorial_function_index, tutorial function indexes as defined in C++ and sent to LUA.`  
`              EXE, object, Object functions as defined in C++ and sent to LUA.`  
`              EXE, sit_conditions, conditions for missions as defined in C++ and sent to LUA.`  
`              EXE, sit_coverage_state, coverage states as defined in the C++ and sent to LUA.`  
`              EXE, automata_states, automata states as defined in the C++ and sent to the LUA.`  
`              EXE, automata_groups, automata groups as defined in the C++ and sent to LUA.`  
`              EXE, building_groups, building groups defined by 16 bit values in the C++ and sent to LUA.`  
`              EXE, reward_state, reward states as defined in C++ and sent to LUA.`  
`              EXE, building_conditions, buildings conditions  as defined in C++ and sent to LUA.`  
`              EXE, zone_tool_types, tool types for zones  as defined in C++ and sent to LUA.`  
`              EXE, game_trends, game trends such as HQ  as defined in C++ and sent to LUA.`  
`              EXE, zodiac, Mysim zodiacs  as defined in C++ and sent to LUA.`  
`              EXE, mysim_trip_types, mysim trip types  as defined in C++ and sent to LUA.`  
`              EXE, game_difficulty_level, difficulty  as defined in C++ and sent to LUA.`  
`              EXE, mysim_idle_animation_ids, mysim animation ids  as defined in C++ and sent to LUA.`  
`              EXE, disaster_ids, disaster ids as defined in C++ and sent to LUA.`  
`              EXE, game_events, game events as defined in C++.`  
`              EXE, game_commands, game commands as defined in C++.`  
`              EXE, network_types, network types as defined in C++.`  
`              EXE, neighbor_deal_types, neighbour deal types as defined in C++.`  
`              EXE, button_tool_types,  button tool types as defined in C++.`  
`              EXE, effects, effects as defined in C++.`  
`              EXE, budget_window_types, budget window types as defined in C++.`  
`              EXE, map_window_types, map window types as defined in C++.`  
`4A5E8F3F - LUA - Generators,Attractors,Repulsors, and System LUAs`  
`           Children`  
`              LUA, dofile, Dofile commands load a file by hashed name translated to instance.`  
`              TRK, GUID, in SFX tables, TRK instances may be called in from 0xAA4d1930 GID to be used specifically.`  
`              BMP, csi_image, A bitmap instance may be used for specific types of definitions in a controller.`  
`              Exemplar, source_building, an exemplar building may be referenced for use in a controller.`  
`              LUA, function, functions can be used to indirectly call a LUA and connect them.`  
`              EXE, cmd, the exe may be referenced by a CMD command to perform a call such as a control movement for a vehicle.`  
`              Effect Dir, fx, the fx command allows to reference an effect inside the effect dir from an LUA.`  
`           Parent`  
`              LUA, dofile, Dofile commands load a file by hashed name translated to instance.`  
`              LUA, function, functions can be used to indirectly call a LUA and connect them.`  
`              Effect Dir, String, Section 6 strings link to repulsors/Attractors/OccupantGroups.`  
`              Itself, ID, At start of file, "--#-package:01234567# -- package signature" the package ID must be unique for all LUA.`  
`              Itself, rawget, line in following format:`  
`                      [if not rawget(globals(), "_unique_name_here") then _unique_name_here = 1]`  
`              EXE, As needed can call directly`  
`           Dependant`  
`              LUA, function, A function declared and created in one LUA can be run from another LUA to reference and call.`  
`              LUA, automata, An LUA may declare an automata group from another file be affected by it.`  
`              LUA, anims, An LUA may declare an animation type from another file be used.`  
`              LUA, controllers, An LUA may declare a controller(generator,attractor etc) from another LUA be used.`  
`              EXE, part of the EXe may be called by a classid definition.`  
`              EXE, effect trigger ID, inside an effect table, an ID may be defined to the exe that can be triggered later.`

**MAD**

`00000001 - Movie Files`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, Loaded by Executable as needed.`

**MXF**

`xxxxxxxx - Font File (does not have TGI)`  
`           Children`  
`              NONE`  
`           Parent`  
`              INI, Assignment, Purpose decided by the Font.ini file. Called directly by the EXE as needed.`

**PNG**

`00000001 - PNG - Main Button Images`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, multi-imaged PNGs called by the exe for the main UI buttons and icons.`  
`1ABE787D - PNG - User Interface (Button and Menu States, Query edges, States)`  
`           Children`  
`              NONE`  
`           Parent`  
`22DEC92D - PNG - Built-In Tools User Interface`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, multi-imaged PNGs called by the exe for the UI Creator.`  
`46A006B0 - PNG - UI Images (UDI, Main Interface, Mysim)`  
`           Children`  
`              NONE`  
`           Parent`  
`4C06F888 - PNG - UDrive Icons`  
`           Children`  
`              NONE`  
`           Parent`  
`              Exemplar, property, `  
`6A1EED2C - Region View City Tiles`  
`           Children`  
`              NONE`  
`           Parent`  
`              EXE, called by the exe when needed for default tiles.`  
`6A386D26 - PNG - Menu Building Icons, Bridges, Overlays`  
`           0xABBBBCCC - Menu images`  
`              Children`  
`                 NONE`  
`              Parent`  
`                 Exemplar, property, `  
`           0xAA0000BB - Bridge Icons`  
`              Children`  
`                 NONE`  
`              Parent`  
`                 Exemplar, property, `  
`           0x0000AAAA - Pinkscreen box overlay`  
`              Children`  
`                 NONE`  
`              Parent`  
`8b6b7857 - Lot Editor PNG Images`  
`           Children`  
`              NONE`  
`           Parent`  
`              Exemplar, property, `  
`A9179251 - PNG - Art picture and their Overlay`  
`           Children`  
`              NONE`  
`           Parent`  
`AB7E5421 - PNG - MySim Thought Bubbles and Transit Icons`  
`           Children`  
`              NONE`  
`           Parent`  
`ebdd10a4 - ?`  
`           Children`  
`              NONE`  
`           Parent`

### R - Z

**RUL**

`aa5bcf57 - Network Rules`  
`           Children`  
`              FSH, Instance, The second rep in each 0x3 line is an IID of a network FSH file.`  
`              Exemplar, Instance, The second rep in each 0x3 line is an IID of a network exemplar file.`  
`              SC4Path, Instance, The second rep in each 0x3 line is an IID of a network SC4path file.`  
`           Parent`  
`              EXE, called during each network plop.`

**Complex RUL**

`aa5bcf57 - Complex Network Rules`  
`           Children`  
`              FSH, Instance, the overrides rules 4 id properties may reference a FSH for a drawn network texture.`  
`              Exemplar, Instance, the overrides rules 4 id properties may reference an exemplar for a 3D network texture.`  
`              FSH, Instance, the solutions rule references a texture FSH for a network by instance.`  
`              Exemplar, Instance, the solutions rule references a texture exemplar for a 3d network by Instance.`  
`           Parent`  
`              EXE, instance, The overrides file is called by Instance ID.`  
`              EXE, instance, The solutions file is called by Instance ID.`  
`              EXE, instance, The intersections file is called by Instance ID.`  
`8a5971c5 - Path remapping`  
`           Children`  
`           Parent`

**S3D**

`badb57f1 - Simglide 3D Model`  
`           0xAAAABCDE - LOD,Object,Arbitrary`  
`              Children`  
`                 FSH, Instances, S3D files link to their textures via the material instance ID in the MATS section.`  
`                 Effect Dir, String, Effects may be called an attached to a model`  
`                      via the effectname property in the REGP section.`  
`                 EXE, prop, S3D files Prop section references the EXE for purposes`  
`                      of determining arbitrary properties for moving models.`  
`              Parent`  
`                 Exemplar, property, models can be referenced by the 0x27812820 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812821 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812822 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812823 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812824 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812920 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812921 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812922 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812923 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812924 property.`  
`                 Exemplar, property, 0x09c80416 property links to an S3D file by resource key.`  
`                 S3D, ResourceKeys, In section 1 a list of resource keys may call random S3D files.`  
`           0xAABBCCDE - 3d Networks (Highway and El/Light)`  
`              Children`  
`                 FSH, Instances, S3D files link to their textures via the material instance ID in the MATS section.`  
`                 Effect Dir, String, Effects may be called an attached to a model`  
`                      via the effectname property in the REGP section.`  
`              Parent`  
`                 Exemplar, property, 3D network pieces are called via the 0x27812820 property resource key`  
`           0xAAAABBCD - Advisors, Fauna`  
`              Children`  
`                 FSH, Instances, S3D files link to their textures via the material instance ID in the MATS section.`  
`                 Effect Dir, String, Effects may be called an attached to a model`  
`                      via the effectname property in the REGP section.`  
`                 EXE, prop, S3D files Prop section references the exe for purposes`  
`                      of determining arbitrary properties for moving models.`  
`              Parent`  
`                 LUA, Advisor_anim_types, this variable defines the IID of an S3D file for various types of animations.`  
`                 Exemplar, property,   0x09c80416 property links to an S3D file by resource key.`  
`           0xAAAABBCC - UDI, disaster, model`  
`              Children`  
`                 FSH, Instances, S3D files link to their textures via the material instance ID in the MATS section`  
`                 Effect Dir, String, Effects may be called an attached to a model`  
`                      via the effectname property in the REGP section.`  
`                 EXE, prop, S3D files Prop section references the exe for purposes`  
`                      of determining arbitrary properties for moving models.`  
`              Parent`  
`                 Exemplar, property, models can be referenced by the 0x27812820 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812821 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812822 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812823 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812824 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812920 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812921 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812922 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812923 property.`  
`                 Exemplar, property, models can be referenced by the 0x27812924 property.`  
`                 Exemplar, property, 0x09c80416 property links to an S3D file by resource key.`  
`                 S3D, ResourceKeys, In section 1 a list of resource keys may call random S3D files.`  
<gen>` - Computer specific BAT Generated S3D model`  
`           Children`  
`              FSH, Instances, S3D files link to their textures via the material instance ID in the MATS section.`  
`              Effect Dir, String, Effects may be called an attached to a model`  
`                   via the effectname property in the REGP section.`  
`           Parent`  
`              Exemplar, property, BAT generated models are referenced by the 0x27812821 property.`

**SC4Path**

`69668828 - Textured Networks Paths`  
`           Children`  
`              NONE`  
`           Parent`  
`              Rule, Instance, The second rep in each 0x3 line is an IID of a network SC4path file.`  
`a966883f - 3D Networks Paths`  
`           0xAABBCCDE`  
`              Children`  
`                 NONE`  
`              Parent`  
`                 Rule, Instance, The second rep in each 0x3 line is an IID of a network SC4path file.`  
`           0xAAAABCCC (for paths on lots)`  
`              Children`  
`                 None`  
`              Parent`  
`                 Exemplar, LotConfig, Property 16 of 0x07 type lotconfig lines where implemented.`

**TRK**

`2a4d1937 - Disaster, Destruction, Siren, Splash, Low Pitch Ambient Effect Sounds`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              HLS, Entry, Any entry in a Hitlist may be a track.`  
`              Effect Directory, Resource Key, Section 9 Sound Resource For Effects.`  
`2a4d193d - Query Sounds`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              Exemplar, Property, 0xAA1DD397 - SFX:Query Sound.`  
`              HLS, Entry, Any entry in a Hitlist may be a track.`  
`aa4d1920 - Activate Sounds & Audio LoopID's & Ambience Decayed & AlarmIDs & HLS Entries`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              Exemplar, Property, 0xABA061F2 - Audio:LoopID`  
`              HLS, Entry, Any entry in a Hitlist may be a track`  
`              Exemplar, Property, 0x0A36AFA2 - SFX:AlarmSoundID`  
`              Exemplar, Property, 0x4a4c132e - SFX:ActivateSound`  
`              Exemplar, Property, 0xCA19D7CA - SFX:Ambience Good Sound`  
`              Exemplar, Property, 0x0a4c13cb - SFX:AmbienceDecayed Sound`  
`              Exemplar, Property, 0x2a53BE13 - SFX:Alarm Ambience Sound`  
`aa4d1930 - ActiveSound & Fireworks, Construction, Sims, UDI, Alien, Crowds, Animals Effects`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered`  
`              HLS, Field, Field 15 of TRK files where entered`  
`              TLO, Field, Field 4 of TRK files where entered`  
`           Parent`  
`              HLS, Entry, Any entry in a Hitlist may be a track.`  
`              Effect Directory, Resource Key, Section 9 Sound Resource For Effects.`  
`              Exemplar, Property, 0x6c044bb5 - SFX:ActiveSound`  
`              LUA, GUID, in LUAs of group 0x4A5E8F3F, a TRK of this GID may be called from inside SFX tables by a GUID var.`  
`ca4d1943 - UI Button Click & Plop Sounds & Wire,Fire, and Tools Effects`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              HLS, Entry, Any entry in a Hitlist may be a track`  
`              Effect Directory, Resource Key, Section 9 Sound Resource For Effects`  
`              UI, Value, btnclicksnd`  
`              UI, Value, btnupsnd`  
`              Exemplar, Property, 0xC9B93A56 - SFX:Default Plop Sound`  
`ca4d1948 - Occupant Instance Sounds`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              Exemplar, Property, 0x6a36afac - SFX:Occupant Instance Sound`  
`              HLS, Entry, Any entry in a Hitlist may be a track`  
`              LUA, mysim_vox, a mysim_vox variable makes a call to the IID of a TRK of this group.`  
`ea4d192a - Fireworks,Riots, Children, Anger, Demo, Crime,Construction, Jet Effects`  
`           Children`  
`              XA, Field, Field 3 of TRK files where entered.`  
`              HLS, Field, Field 15 of TRK files where entered.`  
`              TLO, Field, Field 4 of TRK files where entered.`  
`           Parent`  
`              HLS, Entry, Any entry in a Hitlist may be a track.`  
`              Effect Directory, Resource Key, Section 9 Sound Resource For Effects.`

**Corrupt**

`a8fbd372 - Corrupt Building Lot Exemplar`  
`           Children,Parents as per file.`

**UI**

`08000600 - Main SC4 Interface`  
`           Children`  
`           Parent`  
`96a006b0 - All Game Interfaces Minus the main interface`  
`           Children`  
`           Parent`  
`1d6962cf - SC4 Vanilla Internal Tool Interfaces`  
`           Children`  
`           Parent`  
`              EXE, called by the exe as it was an internal tool.`  
`cb6b7601 - Lot Editor UI's`  
`           Children`  
`           Parent`

**String**

`55555555 - String Texts`  
`           Children`  
`              NONE, Test File`  
`           Parent`  
`              NONE, Test File`

**WAV**

`0a4d1926 - School bell & Fire engine`  
`           Children`  
`              NONE`  
`           Parent`  
`              Effect Dir, Resource Key, Sound resource key for effects in section 9 where filled.`  
`6a4d193a - Fire and Obliterate Sounds`  
`           Children`  
`              NONE`  
`           Parent`  
`              Effect Dir, Resource Key, Sound resource key for effects in section 9 where filled.`

**XA**

`0a4d1926 - Activate Sounds & Audio LoopID`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKS where filled.`  
`0a4d192d - Fireworks,Riots, Children, Anger, Demo, Crime,Construction, Jet Effects`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKs where filled.`  
`              Effect Dir, Resource Key, Sound resource key for effects in section 9 where filled.`  
`0a627909 - Residential Bad Night Small/Medium`  
`           Children`  
`              NONE`  
`           Parent`  
`              LEV, GroupID, Connected to Levels File by Group ID.`  
`2a4d1940 - Query Sounds`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKs where filled.`  
`2a6278ee - Residential Bad Day Large`  
`           Children`  
`              NONE`  
`           Parent`  
`              LEV, GroupID, Connected to Levels File by Group ID.`  
`4a4d1946 - Plop & Button Click & Ambience Decay & Wire,Fire and Tools Effects`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKS where filled`  
`              UI, Value, btnclicksnd`  
`              UI, Value, btnupsnd`  
`6a4d193a - Disaster, Destruction, Siren, Splash, Low Pitch Ambient Effect Sounds`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKs where filled.`  
`              Effect Dir, Resource Key, Sound resource key for effects in section 9 where filled.`  
`8a627912 - Residential Good Day Small/Medium $$$`  
`           Children`  
`              NONE`  
`           Parent`  
`              LEV, GroupID, Connected to Levels File by Group ID`  
`aa4d1933 - Fireworks, Construction, Sims, UDI, Alien, Crowds, Animals Effects`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKs where filled.`  
`              Effect Dir, Resource Key, Sound resource key for effects in section 9 where filled.`  
`aa4d194b - Occupant Instance Sounds`  
`           Children`  
`              NONE`  
`           Parent`  
`              HLS, Entry, Any entry in an HLS may be an XA or TRK.`  
`              TRK, Field, Field 3 of TRKS where filled.`

**XML**

<gen>` - Computer specific Lot Description XML file`  
`           Children`  
`              NONE, however lists required plugin Dats to use this Lot In game. Not actual link. Just theoretical.`  
`           Parent`  
`              EXE, these xml files were created to pass information along`  
`                   between the various parts of the Maxis building tool suite.`

## Unfinished File Types

The file types listed below do not have relational info at this time:

- AB
- AE
- HIT
- complex
- UI
- LTEXT
- FSH
- PNG
- Exemplar
- Cohort
