---
title: "InstanceFormats"
description: ""
published: false
date: '2019-08-04T05:40:34Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-08-03T21:10:07Z'
---

This is a list of all [SimCity 4](/simcity-4) [Group IDs](/group-id) (GID) and the formats of their respective [Instance IDs](/instance-id) (IID) for each Group. To find a specific [file type](/list-of-file-formats) or Group ID, do a find inside this page and it should turn up unless it is a Group ID that is still unknown, or comes from a custom [Lot](/lot) or [BAT](/bat). The reason custom Lots and BATs will not show up here is that the programs used to create these files generate custom Group ID's that are unique to the computer that generated the file, and uses this GID for these items. Consequently, there are as many Group ID's for Lots and BATs as there are content creators, and it would be impractical to list them here. However, those file types that support custom Group ID's will have an entry on this page indicating which custom GID they use. For information about these custom GID's, see the <GEN> and <mGEN> entries at the end of the page.

## Format for GID/IID Entries

**File Type**

<GID>` - `<Group Name>  
`        <instance in format 0xAABBBfCD>`  
`         AA=blah`  
`         BB=blah`  
`         C=blah`  
`         D=blah`

- Characters in the range of A-H are used to show variables that any IID fills. For example, AA for a given IID may be f3,a3,01,00, or any other 2 characters, and so forth.
- A Lowercase letter or a number shows something that doesn't change.
- Some IIDs have a value of 12345678. These predate the use of IID specs by Maxis, and are just placeholders. An Exemplar may have an IID of 00000005. This is a test ID used for automata or Sims. It can also be used for other things however.

## Specification

### A - D

**AB**

`8a5971c5 - UDI Sounds`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Sound Group Family`  
`              C = Sound Group ID`

**AE**

`8a5971c5 - UDI Data`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Data Family`  
`              C = Data File ID`

**ATC**

`2a2458f9 - Props Animation Collections`  
`           0xAABB0000`  
`              A = The animation type (light, sport, etc.)`  
`              B = Animation for that type`  
`49a593e7 - Non-prop Animation Collections`  
`           0xAAABBB00`  
`              A = What Sim/Animation this is for`  
`              B = Action State of this Sim (same for each Sim/Animation)       `  
`                   For example:`  
`                   013 - Protestor holding up sign`  
`                   018 - Protestor with loud speaker`

**AVP**

`2a2458f9 - Props Single Animation `  
`           0xAAAA000B`  
`              A = Instance data from ATC file`  
`              B = Zoom Cycle (starting from 0 upwards at furthest seen zoom)`  
`49a593e7 - Non-Prop Single Animation`  
`           0xAAAAAA0B`  
`              A = Instance data from ATC file`  
`              B = Zoom Cycle (starting from 0 upwards at furthest seen zoom)`

**BMP**

`6a1eed2c - Region tile layout bitmaps`  
`           0xAABBBCCC`  
`              A = Bitmap Family ID`  
`              B = Image Class ID`  
`              C = Incremental Bitmap ID`  
`1d6962cf - SC4 Vanilla Internal Tool Bitmaps`  
`           0xABBBBCDD`  
`              A = Main Bitmap group`  
`              B = Bitmap Type Family`  
`              C = Class. ex. e = Standard button maps.`  
`              D = Incremental ID`  
<gen>` - Computer specific BAT generated overlay picture (small)`  
`           0xAAAA0000`  
`              A = `<mGEN>

**BSPEC**

`aa5bcf57 - Bridge Specification Rules`  
`           0xA000B0CC`  
`              A = Is the Rule a Bridge Specification (1)`  
`              B = Is the Rule a complex rule. (0)`  
`              C = Incremental Hardcoded ID Starting at 1`

**Cohort**

`07BDDF1C - Civic and Park Building Parents`  
`           0xABBBBCCC (Automata Layer Cohorts)`  
`              A = Even number, 0-E `  
`              B = Cohort Family`  
`              C = Cohort ID`  
`           0x0000000A (Main Usage Cohorts)`  
`              A = Cohort ID`  
`096E6739 - Vehicle Type Parents`  
`           0x0000000A (Main Vehicle Cohorts)`  
`              A = Cohort ID`  
`           0xABBBBCCC (Automata Layer Cohorts)`  
`              A = Even number, 0-E `  
`              B = Cohort Family`  
`              C = Automata ID`  
`096e6817 - Watercraft Parents`  
`           0x0000000A`  
`              A = Cohort ID`  
`296e680f - Aircraft Parents`  
`           0x0000000A`  
`              A = Cohort ID`  
`47bddf12 - Zonable Commercial Building Parents`  
`           0xA00000BB`  
`              A = Cohort Zone (if 0, main cohort)`  
`              B = Cohort ID`  
`67bddf0c - Zonable Residential Building Parents`  
`           0xA00000BB`  
`              A = Cohort Zone (if 0, main cohort)`  
`              B = Cohort ID`  
`690f693f - Data view Parents`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = Data Family`  
`              C = Cohort ID`  
`6a297266 - MySim Parent`  
`           0x0000000A`  
`              A = MySim Cohort ID`  
`7a4a8458 - Clouds Parent`  
`           0x0000000A`  
`              A = Tuning Cohort ID `  
`a7bddf17 - Zonable Industrial Building Parents`  
`           0xA00000BB`  
`              A = Cohort Zone (if 0, main cohort)`  
`              B = Cohort ID`  
`a8fbd372 - Building Foundations`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = Foundation Family`  
`              C = Foundation ID`  
`c96e6806 - Crime Simulator`  
`           0x0000000A (Main Sim Affectors)`  
`              A = Incremental Affector ID`  
`           0xABBBBCCC (Sim Cohorts)`  
`              A = Even number, 0-E `  
`              B = Sim Family`  
`              C = Sim ID`  
`ca25875d - Ambience Layer`  
`           0xABBBBCCC (Sim Cohorts)`  
`              A = Even number, 0-E `  
`              B = Ambience Family`  
`              C = Ambience Type ID`  
`ca386e22 - Landmark Parent`  
`           0xABBBBCCC (Sim Cohorts)`  
`              A = Even number, 0-E `  
`              B = Landmark Cohort Family`  
`              C = Cohort ID`

**Config**

`49dd6e08 - SimCity Configuration File (.cfg)`  
`           0x0000000A`  
`              A = Config File Number. Only config file 1 currently exists.`

**Corrupt**

`a8fbd372 - Corrupt Building Lot Exemplar`  
`           Instance as per file.`

**Cursor**

`00000001 - Black & White Cursors`  
`           0xAAAAABBB`  
`              A = Main Cursor type (same for each bit depth)`  
`               '' Types are randomly chosen and are hardcoded`  
`              B = Incremental Cursor Identifier (same for each bit depth)`  
`               '' Identifiers are randomly chosen but usually increment`  
`                  In integers sequentially, for example: 770 = northeast, 771 = east.`  
`00000004 - 4bit Cursors`  
`           0xAAAAABBB`  
`              A = Main Cursor type (same for each bit depth)`  
`               '' Types are randomly chosen and are hardcoded`  
`              B = Incremental Cursor Identifier (same for each bit depth)`  
`               '' Identifiers are randomly chosen but usually increment`  
`                  In integers sequentially, for example: 770 = northeast, 771 = east.`  
`00000008 - 8bit Cursors`  
`           0xAAAAABBB`  
`              A = Main Cursor type (same for each bit depth)`  
`               '' Types are randomly chosen and are hardcoded`  
`              B = Incremental Cursor Identifier (same for each bit depth)`  
`               '' Identifiers are randomly chosen but usually increment`  
`                  In integers sequentially, for example: 770 = northeast, 771 = east.`  
`00000032 - 32bit Cursors`  
`           0xAAAAABBB`  
`              A = Main Cursor type (same for each bit depth)`  
`               '' Types are randomly chosen and are hardcoded`  
`              B = Incremental Cursor Identifier (same for each bit depth)`  
`               '' Identifiers are randomly chosen but usually increment`  
`                  In integers sequentially, for example: 770 = northeast, 771 = east.`

**DBPF**

`6a5b7b57 - DBPF Data files`  
`           0xAAAABBBB`  
`              A = Family ID (usually existing) Has no purpose towards function`  
`              B = Unique ID`  
`               '' These IIDs are hardcoded. The reason for picking an existing`  
`                  Family ID in most cases is probably just for convenience.`

**DIR**

`e86b1eef - Compressed File Directory`  
`           0x286b1f03 - Instance code for DBPF Directory.`

### E - K

**Effect Dir**

`ea5118b1 - Effect Resource Tree`  
`           0xAAAAAAAA`  
`              A = Normally an incremental number from 0 upward, but with the Airforce plugin, Maxis randomly generated one.`

**Exemplar**

`07BDDF1C - Exemplar - Civic and Park Buildings`  
`           0xAAAABBBB`  
`              A = Civic, Building Family`  
`              B = Civic, Unused, for S3d Files`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Park Family`  
`              C = Park ID`  
`084344E0 - Exemplar - Network Placement Tuning Parameters`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Tuning Family`  
`              C = Exemplar ID`  
`088E1962 - Exemplar - Power Poles`  
`           0xAA000BBB`  
`              A = Network Type`  
`              B = Pole Model ID`  
`096E6739 - Exemplar - Land Vehicle Types`  
`           0xAAAABBBB`  
`              A = Vehicle ID`  
`              B = Unused, for S3D's`  
`           0xABBBBCCC (rarely used backup format)`  
`              A = Even number, 0-E `  
`              B = Family`  
`              C = Exemplar ID`  
`096E6817 - Exemplar - Water Vehicle Types`  
`           0xAAAABBBB`  
`              A = Vehicle ID`  
`              B = Unused, for S3D's`  
`           0xABBBBCCC (rarely used backup format)`  
`              A = Even number, 0-E `  
`              B = Family`  
`              C = Exemplar ID`  
`2821ED93 - Exemplar - Bridge Pieces Network Part Assignment`  
`           0xAAAABBBB`  
`              A = Bridge Pieces, Piece ID`  
`                  Light Map, unused`  
`              B = Bridge Pieces, unused, For S3D`  
`                  Light Map, Piece ID`  
`296E680F - Exemplar - Air Vehicle Types`  
`           0xAAAABBBB`  
`              A = Vehicle ID`  
`              B = Unused, for S3D's`  
`           0xAAAAAAAA (test exemplar)`  
`              A = An S3D model.`  
`2989FD57 - Construction Properties`  
`           0xABBBBCCC (rarely used. backup format)`  
`              A = Even number, 0-E `  
`              B = Family`  
`              C = Exemplar ID`  
`29B6C670 - Exemplar - Disasters`  
`           0x0000000A`  
`              A = Incremental disaster ID`  
`           0xABBBBCCC (Rush Hour Disasters)`  
`              A = Even number, 0-E `  
`              B = Family`  
`              C = Exemplar ID`  
`2A3858E4 - Exemplar - Menu Items`  
`           0x00000AAA`  
`              A = Menu Item ID`  
`           0xAAAABBBB (Intersections)`  
`              A = Intersection Family`  
`              B = Intersection ID`  
`2B79DFFB - Exemplar - Light Rail Pieces`  
`           0xAAAAAAAA (test exemplar format)`  
`              A = An S3D model.`  
`           0xAABBCCDE - 3d Networks`  
`              A = Network ID`  
`              B = Piece ID`  
`              C = Underlying Piece ID`  
`              D = Sub ID for complex pieces`  
`              E = Zoom of underlying piece`  
`47BDDF12 - Developer: Commercial`  
`           0xAAAABBBB`  
`              A = Building Family ID`  
`              B = Unused, for S3D's`  
`67BDDF0C - Developer: Residential`  
`           0xAAAABBBB`  
`              A = Building Family ID`  
`              B = Unused, for S3D's`  
`67CD5FA1 - Exemplar - Building Behavior Simulators`  
`           0xABBBBCCC (rarely used backup format)`  
`              A = Even number, 0-E `  
`              B = Zone Family`  
`              C = Developer ID`  
`           0x0000AABB`  
`              A = Zone Type`  
`              B = Wealth Type`  
`690F693F - Exemplar - Dataview and UDrive-It Interfaces`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = Data View Family`  
`              C = View ID`  
`6A01FC2A - Exemplar - God Mode Terrain Tools`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Terrain Modification Family`  
`              C = Visual Effect ID`  
`6A297266 - Exemplar - MySims`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Sim Family`  
`              C = Sim ID`  
`7A4A8458 - Exemplar - Tuning Parameters/Background Loaders`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Tuning Family`  
`              C = Tuning Table ID`  
`88CD66E9 - Exemplar - Fluid Dynamics Properties`  
`           0x0000000A`  
`              A = Dynamics Type ID`  
`8974F80F - Exemplar - Supports`  
`           0xAABBCCDD`  
`              A = Main Network Type`  
`              B = Piece Family`  
`              C = Support Piece ID`  
`              D = Unused, for Textures`  
`89AC5643 - Exemplar - Transit Pieces (except light rail)`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Piece Family`  
`              C = Piece ID`  
`89C2A517 - Exemplar - Textures`  
`           0x000000AA`  
`              A = Texture ID`  
`8A3858D8 - Exemplar - Rewards`  
`           0xAAAABBBB`  
`              A = Building ID`  
`              B = Unused, for S3D's        `  
`A7BDDF17 - Developer: Industrial`  
`           0xAAAABBBB`  
`              A = Building ID`  
`              B = Unused, for S3D's        `  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Field Family`  
`              C = Field ID`  
`A82CA30F - Exemplar - Bridge Pieces Main Definition`  
`           0xAA0000BB`  
`              A = Network ID`  
`              B = Bridge ID`  
`A8434037 - Exemplar - Highway Pieces Definitions`  
`           0xAABBCCCC`  
`              A = Network ID`  
`              B = Bridge Piece Family`  
`              C = Bridge Piece ID`  
`A8FBD372 - Exemplar - Building Lots`  
`           0xAAAABBBB`  
`              A = Lot Family`  
`              B = Lot ID`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Lot Family`  
`              C = Lot ID`  
`A9189CF0 - Lighting Exemplar`  
`           0x0000000A`  
`              A = Exemplar ID`  
`A998D30B - Automata Tuning Exemplar`  
`           0x0000000A`  
`              A = Tuning Exemplar ID`  
`A9C2C209 - Exemplar - Ordinances`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Ordinance Family`  
`              C = Ordinance ID`  
`C7BB4816 - Exemplar - Demand Simulator`  
`           0x0AAAABCD`  
`              A = Relation Family (R, CO, ID etc. Format: 00##)`  
`              B = Data Class (Census, Workforce, etc)`  
`              C = Wealth`  
`              D = Data Type (EQ1,2,3 etc.)`  
`C8DBCCBA - Exemplar - Utility Buildings`  
`           0xAAAABBBB`  
`              A = Building ID`  
`              B = Unused, for S3D's        `  
`C96E6806 - Exemplar - Crime Props`  
`           0xAABB0000`  
`              A = The animation type (light, sport, etc.)`  
`              B = Animation for that type`  
`           0xAAABBB00`  
`              A = What Sim/Animation this is for`  
`              B = Action State of this Sim (Same for each Sim/Animation)       `  
`                    for example:`  
`                      013 - Protestor holding up sign`  
`                      018 - Protestor with loud speaker`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Sim Family`  
`              C = Sim ID`  
`C977C536 - Exemplar - Props`  
`           0xAAAABCCC`  
`              A = LODs, Prop ID`  
`                  Effect, Prop ID`  
`              B = LODs, Foundation Flag`  
`                  Effect, Effect number`  
`              C = Unused, for S3D's`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Prop Family`  
`              C = Prop ID`  
`CA25875D - Exemplar - Ambiance Layer Functionality`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Layer Family`  
`              C = Ambient ID`  
`CA386E22 - Exemplar - Landmarks`  
`           0xAAAABBBB`  
`              A = Building ID`  
`              B = Unused, for S3D's        `  
`CA4AD545 - Exemplar - Graphs`  
`           0x000000AA`  
`              A = Graph ID`  
`CB730FAC - Exemplar - Avenue Bridge Pieces Resources`  
`           0xAAAABCCC`  
`              A = Piece ID`  
`              B = Section Flag (Support, or Connector)`  
`              C = Unused, for S3D's`  
`CBE084CB - Exemplar - One way Network Intersections & Road Tunnel`  
`           0xAABBCC00`  
`              A = Network ID`  
`              B = Intersection Type`  
`              C = Piece ID`  
`E7E2C2DB - Exemplar - Simulators`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Simulator Family`  
`              C = Simulator ID`  
`E8347989 - Exemplar - Rail & Highway Bridge Pieces Resources & Rail Tunnel`  
`           0xAAAABCCC`  
`              A = Piece ID`  
`              B = Section Flag (Support, or Connector)`  
`              C = Unused, for S3D's`  
`E83E0437 - Exemplar - Trees`  
`           0xAAAABBCC`  
`              A = Flora Family`  
`              B = Flora Type`  
`              C = Flora ID`  
`EA12F32C - Exemplar - Crimes`  
`           0x000000AA`  
`              A = Crime ID`  
`EBE084C2 - Exemplar - 3D Transportation Pieces - Monorail/Light Rail`  
`           0xAAAABB00`  
`              A = Piece Family`  
`              B = Piece ID`  
`EBE084d1 - Exemplar - 3D Transportation Pieces - Ground Highway`  
`           0xAAAA0000`  
`              A = Piece ID`  
<gen>`  - Computer specific Plugin Manager or PIM-X generated Group ID for custom content.`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Lot Family`  
`              C = Lot ID`

**FSH**

`0986135E - FSH - Base and Overlay Textures`  
`           0xAAAABCDE`  
`              A = OverLay/Base ID`  
`              B = Wealth`  
`              C = Descriptor (Controls State, and things like Zone Tile Part Number's)`  
`              D = Unused, or a 0 on the end of the Descriptor. Your Choice.`  
`              E = Zoom`  
`1ABE787D - FSH - Building Textures/Bridge Textures/Misc Textures/Network Textures`  
`           0xAABBCCDE - Network Textures`  
`              A = Network ID`  
`              B = Piece Family`  
`              C = Piece ID`  
`              D = Border Texture Type`  
`              E = Zoom`  
`           0xAAAABCDE - LODs (Buildings, Props etc.)`  
`              A = LOD ID`  
`              B = Light (8 or sometimes 9) Flag`  
`              C = Zoom`  
`              D = Rotation`  
`              E = Texture Frame`  
`           0xAAAABCD0 - Flora`  
`              A = Flora ID`  
`              B = Light (8) Flag`  
`              C = Zoom`  
`              D = Model Variant`  
`           0xAAAA000B - Graffiti (1dc##### in SimCity_2.dat)`  
`              A = Graffiti ID`  
`              B = Graffiti Flag (Should be set to 1)`  
`           0xABBBBCCC - Sims, Automata, Fauna, Masks, and Clouds`  
`              A = Even number, 0-E`  
`              B = Texture Family (a624/a478 - clouds, c35f explosions)`  
`              C = Texture ID`  
`           0xAAAAB00C - Construction & Materials Textures`  
`              A = Texture Group (Construction and Material)`  
`              B = ID of Texture`  
`              C = Zoom`  
`2A2458F9 - FSH - Animation Sprites for Props`  
`           0xAABB0000`  
`              A = The animation type (light, sport, etc)`  
`              B = Animation for that type`  
`2BC2759A - FSH - Transit Piece Masks`  
`           0xAABBCCCE`  
`              A = Network ID`  
`              B = Piece Family`  
`              C = Piece ID `  
`              D = Zoom`  
`49A593E7 - FSH - Animation Sprites non Props`  
`           0xAAABBB00`  
`              A = What Sim/Animation this is for`  
`              B = Action State of this Sim (Same for each Sim/Animation)       `  
`                   for example:`  
`                     013 - Protestor holding up sign`  
`                     018 - Protestor with loud speaker`  
`891B0E1A - FSH - Terrain & Foundation Textures/Masks/Effect Textures`  
`           0x0000AAAA - Terrain`  
`              A = Texture ID`  
`           0xABBBBCCC - Masks & Effects`  
`              A = Even number, 0-E`  
`              B = Texture Family`  
`              C = Texture ID`  
`           0xAAAA000B`  
`              A = Foundation ID`  
`              B = Zoom`  
`cb6b7bd9 - Lot Editor Arrow Images`  
`           0xAABBBBCC`  
`              A = Image Group ID`  
`              B = Image Family ID`  
`              C = Image ID`  
`46A006B0 - FSH - User Interface Images`  
`           0xAABBBCCC`  
`              A = Main Group`  
`              B = UI/Menu Family`  
`              C = Image ID`  
<gen>` - Computer specific BAT generated Texture groupid`  
`           0xAAAABCDE`  
`              A = `<mGEN>  
`              B = Normal Map (0) or Lighting Map (8)`  
`              C = Zoom`  
`              D = Rotation`  
`              E = FSH frame number`

**HIT**

`ca4d19e3 - HIT Audio Track Data`  
`           0xABBBBCCC`  
`              A = HIT Group`  
`              B = HIT Family`  
`              C = Unique ID`  
`               ''Linked to TLO by Group ID. No Grouping. Single File.`

**HLS**

`9dbdbf74 - Sound Hitlists`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Hitlist Family`  
`              C = Unique ID`

**INI**

`4a87bfe8 - Font INI`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Family ID (usually existing), has no purpose towards function`  
`              C = Unique ID`  
`               ''These IIDs are hardcoded. The reason for picking an existing Family ID in most cases is probably just for convenience.`  
`8a5971c5 - Terrain Mapping & Path Remapping, Sound, and Features INI`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Family ID (usually existing) Has no purpose towards function`  
`              C = Unique ID`  
`               ''These IIDs are hardcoded. The reason for picking an existing Family ID in most cases is probably just for convenience.`

**JFIF/JPEG**

`ca133ecb - JPEG Art`  
`           0xAaBBCCDE`  
`              A = Main Picture Group`  
`              B = Subgroup, for example: 5e = normal, 39 = horizontally squished`  
`              C = Class, for example: 3e = In-game art`  
`              D = Subclass, for example: D = RCI`  
`              E = Picture ID`  
<gen>` - Computer specific BAT generated overlay picture (large)`  
`           0xAAAA0000`  
`              A = `<mGEN>

**KEYCFG**

`6a231eaa - Accelerator Tables`  
`           0xAAAAAABB`  
`              A = Key Family ID`  
`              B = Key Map Member ID`

### L - R

**LEV and XA** (XAs currently in the LEV area)

`0a5bcda5 - Construction`  
`           0xABBBBCCC`  
`              A = Family ID of Sound. Sound groupings. Char 0-F`  
`               `*`May change in an LEV/XA group`*  
`              B = Sound Group for this Family (i.e. subway, farm)`  
`               `*`May change for files in an LEV`*  
`              C = Sound ID for this Group (i.e. loud subway, soft, etc.)`  
`               `*`For LEVs, this is usually higher than the last sound for that Group`*  
  
`The following Group ID's all use the same Instance Format described above:`  
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

**LogicObject**

`ca4d19e3 - Track Logic Object (TLO)`  
`           0xABBBBCCC`  
`              A = Logic Object Associated Group`  
`              B = Logic Object Associated Family ID`  
`              C = TLO Unique ID`

**Lot Data** (LD or LDAT)

`6be74c60 - Exchange Data for Lot`  
`           0x0000000A`  
`              A = 1. A hardcoded value for each lot file declaring the exchange file`

**LTEXT** LTEXT files in plugins have incremental GID's to signify different languages to the .exe.

`EA5524EB - LTEXT - Misc. Item Names/Descriptions`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`EA231E96 - LTEXT - Misc. Texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`CA554B03 - LTEXT - Popup window HTML texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`8A635D24 - LTEXT - Audio file name to description texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`8A5E03EC - LTEXT - Disaster texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`8A4924F3 - LTEXT - About SC4 window HTML text`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`6A554AFD - LTEXT - Misc. Item Names/Descriptions`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`6A3FF01C - LTEXT - Game UI Texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`6A231EAA - LTEXT - Interactivity Feature Texts (MySim, UDriveIt, etc.)`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`6A231EA4 - LTEXT - News ticker message texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`4A5E093C - LTEXT - Terrain tool texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`4A5CB171 - LTEXT - Funny random city loading message texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`2A592FD1 - LTEXT - Item plop/draw notification texts`  
`           0xA00000BB`  
`              A = Text Type (A = intersection draws, F = Failed draws, and Tips)`  
`              B = Text ID`  
`0A554AF5 - LTEXT - Audio UI Panel texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`0A554AE8 - LTEXT - General UI texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`0A554AE0 - LTEXT - Item visible name and description texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`0A419226 - LTEXT - In game error texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`6a4eb3f7 - LTEXT - Population Text`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
`EAFCB180 - LTEXT - Plugin Install Text`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = Text Family`  
`              C = Text ID`  
  
`6a231eaa - `**`De-Localizer`**` - used to avoid language localization.`  
`           Located in the same Group as LTEXTs, but not actually text.`  
`           0a6df4df - IID for De-Localizer`

**LUA**

`4A5E8EF6 - LUA - Missions, Advisors, Tutorials and Packaging files)`  
`           0xAABBBBBB`  
`              A = ff. The code for LUA script.`  
`              B = 24 bit Hash for use in Dofiles`  
`4A5E8F3F - LUA - Generators, Attractors, Repulsors, and System LUAs`  
`           0xAABBBBBB`  
`              A = ff. The code for LUA script.`  
`              B = 24 bit Hash for use in Dofiles`

**MAD**

`00000001 - Movie Files`  
`           0xAAAAAAAA`  
`              Incremental ID. Hardcoded for main dats.`

**PNG**

`00000001 - PNG - Main Button Images`  
`           0xAABBBCCC`  
`              A = Main Group (13 = Bottom UI, 14 = Everything Else)`  
`              B = UI/Menu Family`  
`              C = Image ID`  
`1ABE787D - PNG - User Interface (Button and Menu States, Query edges, States)`  
`           0xAABBBCCC`  
`              A = Main Group`  
`              B = UI/Menu Family`  
`              C = Image ID`  
`22DEC92D - PNG - Built-In Tools User Interface`  
`           0x0000AAAA`  
`              A = Image ID (000#, 100#, 200#, and 300# series are used)`  
`46A006B0 - PNG - UI Images (UDriveIt, Main Interface, MySim)`  
`           0xAABBBCCC`  
`              A = Main Group`  
`              B = UI/Menu Family`  
`              C = Image ID`  
`4C06F888 - PNG - UDriveIt Icons`  
`           0xAAAABB00`  
`              A = Main ID (Either the vehicle or Sim the icon is concerned with)`  
`              B = Transport ID (What vehicle or device is transporting the Sim)`  
`6A1EED2C - Region View City Tiles`  
`           0xAABBBCCC`  
`              A = Tile Size`  
`              B = Image Class (231 is Tile Maps)`  
`              C = Image ID (For Tilemaps: Water, Land, Overlay)`  
`6A386D26 - PNG - Menu Building Icons, Bridges, Overlays`  
`           0xABBBBCCC - Menu images`  
`              A = Image Grouping.`  
`              B = Image Menu Family (Parks, Civic, etc.)`  
`              C = Image Button ID (The specific ID of this Buildings Image)`  
`           0xAA0000BB - Bridge Icons`  
`              A = Network ID`  
`              B = Bridge ID`  
`           0x0000AAAA - Pinkscreen box overlay`  
`              A = Arbitrary Image ID. Only used for a 'pinkscreen' image.`  
`8b6b7857 - Lot Editor PNG Images`  
`           0xAABBBBCC`  
`              A = Image Group (Kind of image)`  
`              B = Image Family (Where image will be used)`  
`              C = Image ID`  
`A9179251 - PNG - Art pictures and their Overlays`  
`           0xAABBBCCC`  
`              A = Main Group (09 for these pics)`  
`              B = Art Image Family`  
`              C = Image ID`  
`AB7E5421 - PNG - MySim Thought Bubbles and Transit Icons`  
`           0xAABBBCCC`  
`              A = Bubble or Icon Group (B&W, Mood, Bubble Overlay)`  
`              B = Bubble or Icon Family (For combo groups, subgroup)`  
`              C = Bubble or Icon ID`  
`ebdd10a4 - PNG - Lot Pictures`  
`           0xABBBBCCC`  
`              A = Image Grouping.`  
`              B = Image Family`  
`              C = Image ID (The specific ID of this building's image)`

**RUL**

`aa5bcf57 - Network Rules`  
`           0xA000B0CC`  
`              A = Is the Rule a Bridge Specification (0)`  
`              B = Is the Rule a complex rule (0)`  
`              C = Incremental, hardcoded ID starting at 1`  
`aa5bcf57 - Complex Network Rules`  
`           0xA000B0CC`  
`              A = Is the Rule a Bridge Specification (0)`  
`              B = Is the Rule a complex rule (1)`  
`              C = Incremental, hardcoded ID Starting at 1`

### S - Z

**S3D**

`badb57f1 - Simglide 3D Model`  
`           0xAAAABCDE - Standard Instance Format`  
`              A = LODs, LOD Model ID`  
`                  Object, 3D Object ID (Cars, complex 3d objects, etc)`  
`                  Arbitrary Assign, AssignID (All other values unused)`  
`              B = LODs, Foundation flag (is foundation or not)`  
`                  Object, TypeFlag (0 = vehicle, 1= rear light, 2 = vehicle lights, 3 = siren, 5 = General 3d model)`  
`              C = LODs, Zoom`  
`                  Object, unused`  
`              D = LODs, Rotation`  
`                  Object, unused`  
`              E = LODs, unused`  
`                  Object, Secondary Typeflag (as main type flag)`  
`           0xAABBCCDE - 3D Networks`  
`              A = Network Type (02 highway, 08 Light rail)`  
`              B = Highway, Piece Class (00 Single or 01 Intersection)`  
`                  El Rail/Light Rail, Piece ID`  
`              C = Highway, Piece ID`  
`                  El Rail/Light Rail, Underlying Network Piece ID`  
`              D = Highway, SubID (for things like Clovers, the part of the clover)`  
`                  El Rail/Light Rail, Where used, the SubID as above`  
`              E = Highway, Zoom of Underlying Network Piece`  
`                  El Rail/Light Rail, Zoom of Piece`  
`           0xAAAABBCD - Advisors, Fauna`  
`              A = Fauna, Fauna Family ID`  
`                  Advisor, Advisor Class ID (2a42) or Mission ADV Classid (ec20)`  
`              B = Fauna, Model State`  
`                  Advisor, Normal (b5) or Llama (b6) or DrVu (24, for missions)`  
`              C = Fauna, Use Seperate Alpha? Flag (0,1)`  
`                  Advisor, Advisor Number`  
`              D = Fauna, Map if Seperation flag is on (2 = alpha, 4 = normal)`  
`                  Advisor, Advisor Mood`  
`           0xAAAABBCC - UDI, Disaster, Simple 3D model`  
`              A = Family ID`  
`              B = UDI, State`  
`                  Disaster, Disaster ID`  
`                  Simple 3d Model, Model Class`  
`              C = Model ID`  
<gen>` - Computer specific BAT Generated S3D model`  
`           0xAAAABCD0`  
`              A = `<mGEN>  
`              B = Foundation flag`  
`              C = Zoom`  
`              D = Rotation`

**SC4Path**

`69668828 - Textured Networks Paths`  
`           0xAABBCCDD`  
`              A = Main Network Type`  
`              B = Path Family (For roads, 01 = straight to diagonal intersection, 02 = odd cross)`  
`              C = Network Piece ID`  
`              D = Unused, for Textures`  
`a966883f - 3D Networks Paths`  
`           0xAABBCCDE`  
`              A = Main Network Type`  
`              B = Path Family`  
`              C = Network Piece ID`  
`              D = For Construct sections, the part of the construct network section`  
`              E = Unused, for Textures where applicable`  
`           0xAAAABCCC (for paths on lots)`  
`              A = Building Family ID`  
`              B = Foundation Flag (only used once in paths)`  
`              C = Unused, for S3D LOD files`

**String**

`55555555 - String Texts`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = String Family `  
`              C = String ID`

**TRK**

`2a4d1937 - Disaster, Destruction, Siren, Splash, Low Pitch Ambient Effect Sounds`  
`           0xABBBBCCC`  
`              A = Even number, 0-E`  
`              B = TRK Family `  
`              C = TRK File ID`  
  
`The following Group ID's all use the same Instance Format described above:`  
`2a4d193d - Query Sounds`  
`aa4d1920 - Activate Sounds, Audio Loop ID's, Ambience Decayed, and HLS Entries`  
`aa4d1930 - Fireworks, Construction, Sims, UDI, Alien, Crowds, Animals Effects`  
`ca4d1943 - UI Button Click & Plop Sounds & Wire,Fire, and Tools Effects`  
`ca4d1948 - Occupant Instance Sounds`  
`ea4d192a - Fireworks, Riots, Children, Anger, Demo, Crime, Construction, Jet Effects`

**UI**

`08000600 - Main SC4 Interface`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = UI Family (9923 = Main Menu Secondary Menu Bitmaps)`  
`              C = UI ID`  
`96a006b0 - All Game Interfaces except the main interface`  
`           0xABBBBCCC`  
`              A = Even ID 0-E`  
`              B = UI Family (c1d7 = UDI Control Windows)`  
`              C = UI ID`  
`1d6962cf - SC4 Vanilla Internal Tool Interfaces`  
`           0xAAABBBBB`  
`              A = UI group. 'ace' is standard`  
`              B = Incremental ID starting from 0 as needed`  
`cb6b7601 - Lot Editor UI's`  
`           0xABBBBCCC`  
`              A = Even number, 0-E `  
`              B = UI Family `  
`              C = UI ID`

**WAV**

`0a4d1926 - School bell and fire engine`  
`           0xABBBBCCC`  
`              A = Family ID of Sound. Sound groupings.`  
`              B = Sound Group for this Family (i.e. subway, farm)`  
`              C = Sound ID for this Group (i.e. loud subway, soft, etc.)`  
`6a4d193a - Fire and Obliterate Sounds`  
`           0xABBBBCCC`  
`              A = Family ID of Sound. Sound groupings.`  
`              B = Sound Group for this Family (i.e. subway, farm)`  
`              C = Sound ID for this Group (i.e. loud subway, soft, etc.)`

**XA**

`0a4d1926 - Activate Sounds & Audio Loop ID`  
`           0xABBBBCCC`  
`              A = Family ID of Sound. Sound groupings.`  
`              B = Sound Group for this Family (i.e. subway, farm)`  
`              C = Sound ID for this Group (i.e. loud subway, soft, etc.)`  
  
`The following Group ID's all use the same Instance Format described above:`  
`0a4d192d - Fireworks,Riots, Children, Anger, Demo, Crime,Construction, Jet Effects`  
`0a627909 - Residential Bad Night Small/Medium`  
`2a4d1940 - Query Sounds`  
`2a6278ee - Residential Bad Day Large`  
`4a4d1946 - Plop & Button Click & Ambience Decay & Wire,Fire and Tools Effects`  
`6a4d193a - Disaster, Destruction, Siren, Splash, Low Pitch Ambient Effect Sounds`  
`8a627912 - Residential Good Day Small/Medium $$$`  
`aa4d1933 - Fireworks, Construction, Sims, UDI, Aliens, Crowds, Animals Effects`  
`aa4d194b - Occupant Instance Sounds`

**XML**

<gen>` - Computer specific Lot Description XML file`  
`           0xAAAAAAAA `  
`              A = Same as applicable parent file for each of .SC4model, Lot, Desc`  
`                  For example, Model = main S3D, Lot = main exemplar, Desc = main exemplar`

### <GEN> and <mGEN>

**<GEN>** and **<mGEN>** are generated ID's that are specific and unique to a computer and are designated at the time that particular modding tools are installed. The Model ID <mGEN> is the first 2 bytes of the Instance ID of models and textures. The Group ID <GEN> is the custom GID for the models, textures, exemplars, xml's and pictures created on that particular computer. Its purpose is to add yet another random factor to building design so that buildings don't conflict (due to the fact that the TGI's follow standard naming). The <GEN> is designated using the following method: a huge random number over 2^29 DWORD is overlayed with a bit flag by a DWORD of timestamp starting around 1997 (the time EA bought Maxis). The generated Model ID <mGEN> is an incremental number that represents the building Family ID. It starts at 0001.

A note on 1 character Family, "Even" or Group IDs as seen in various instances. These appear to be used some times specifically, however they go from 0 to E and often appear randomly chosen as a way to vary the instances more.
