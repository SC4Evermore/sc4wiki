---
title: "Network Specs/IntersectionOrdering RUL"
description: ""
published: false
date: '2019-08-04T05:45:29Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2009-01-25T05:07:20Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Network Specs/IntersectionOrdering RUL</th></tr>
<tr><td><strong>Name</strong></td><td>Intersection Ordering RUL</td></tr>
<tr><td><strong>Format</strong></td><td><a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x0A5BCF4B</td></tr>
<tr><td><strong>Group</strong></td><td>0xAA5BCF57</td></tr>
<tr><td><strong>Instance</strong></td><td>0x10000000</td></tr>
<tr><td><strong>Comments</strong></td><td><em>See also: </em></td></tr>
</table>
</div>

RUL (INI file type) 0x10000000, **Intersection Ordering**.

## Intersection Ordering

    RotationRing = hex-id [,hex-id...]

Creates a ring of rules that are cycled through via Home/End keys or automatically by the tool as it tries to auto-fit rules to the current mouse point.

    AddTypes = hex-id [,hex-id...]

Attaches another ring to the last ring, creating type rings perpendicular to the rotation ring. Type rings can be cycled through via Tab/Shift-Tab. Generally, type rings are set up to preserve rotation as you cycle through rules of different network types.

A given rule can only belong to ONE rotation ring and ONE type ring. Attempting to hook a rule into more than one rotation or type ring will result in the rings getting trashed.

|  |  |  |  |
|----|----|----|----|
| RotationRing | = | 2000, 2001, 2051, 2002, 2003, 2052, 2004, 2005, 2053, 2006, 2007, 2050 | el3 / el3offset |
| AddTypes | = | 2010, 2011, 2059, 2012, 2013, 205A, 2014, 2015, 205B, 2016, 2017, 2058 | gh3 / gh3offset |

Essentially all of the rotations of a given intersection type are put on a single line, in clockwise order, using the RotationRing or AddTypes functions. The different items (ramps, interchanges, etc) are placed on successive lines so that you can tab through the network items, or home/end through the rotations. The difference between RotationRing & AddTypes is; RotationRing is used to define the start of a section, or button. Whereas AddTypes is used for the successive items attached to that RotationRing. So having only one RotationRing & 10 AddTypes following it below is perfectly normal.

RotationRings & AddTypes: If added, these should match the \#InstanceIDHere# from below. To create a functional Menu button for a given Interchange/junction, the RotationRing/AddTypes value is used \[the Item Button ID property can also be used to link directly to \[HighwayIntersectionInfo_InstanceIDHERE\] value, though it’s advisable not to do such a thing for general purposes\]. The Exemplar Property for this is the Item Button ID \[0x8A2602BB\]. The first four values of this property must be 0x6A47 . The last four values of this property must match the RotationRing/AddTypes value \[best way to do this is to just use an existing Exemplar file, of the same type, as a template to do this. Just be sure to change the Instance ID of the [Exemplar](/exemplar) file at least, otherwise conflicts will arise\].

- **Note:** Specific Network Naming functions (i.e. "Road", "Rail", "LightRail", "Subways", etc) that are valid in one [RUL](/rul) file by the [SimCity 4](/simcity-4) engine, can be valid in another RUL file. Sometimes the order in which a function or naming function is used/placed though can depend on whether its associated components will work come run-time.

The entire rest of the file consists of \[HighwayIntersectionInfo_InstanceIDHERE\] lines. The [Instance IDs](/instance-id) for these sections all have zeros in the first four places. This is necessary for anything ploppable, because of the way the buttons call the rotationrings/addtypes. Each interchange/overpass/junction/etc, must have a unique \#instanceIDhere# value, otherwise conflicts will arise, and some/all of the rules with the same \#instanceIDhere# value will not work.

Maxis' comments say this:

    ;--------------------------------------------------------
    ; Highway intersection rules.
    ;
    ;   StepOffsets = start-offset, end-offset
    ;   PaddingCell = x-offset, z-offset, edge-types
    ;   CellLayout  = <mix of characters>
    ;                 '+': Add invisible tile for piece
    ;                 'n': Tile must be a new network tile from current drag
    ;                 'p': Tile must be a previously existing network tile
    ;                 'X': Both 'n' and 'p' apply (intersection tile)
    ;                 '.': Don't care
    ;                 'P': Padding tile
    ;                 '<': Set center row
    ;                 '^': Set center column
    ;   CopyFrom    = source-rule-ID
    ;   Invert      = 1
    ;   Transpose   = 1
    ;   ConvertQueryID = string-instance-id
    ;   PlaceQueryID   = string-instance-id

- **Note:** In practice, not all the mentioned functions are actually used, or used properly, in the RUL file. Some items are related to Vanilla SC4 (Pre-RH). If you have a copy of both Pre & Post SC4 RH, you will notice that this particular area of the game underwent significant (file format) changes, and some functions have been affected as a result.

## The Translation

Let's look at an actual interchange RUL and pull it apart, piece by piece. That will allow us to understand it more easily.

The following item has been extracted from the IntersectionOrdering, but with some changes.

`[HighwayIntersectionInfo_0x00002130]`

This defines the Instance ID of the given interchange. The text before the ID must remain as "HighwayIntersectionInfo\_" or else the RUL will not be recognized.

`Piece = 8.0, 8.0, 0, 0, 0x02012300`

The **Piece** line stipulates the Point of Focus for the Cursor in reference to the Preview Model:

`Format: Piece = X=W/E, Y=N/S, Rotation, Flip, 0x02012300`

`Positive X=East, Negative X=West, Positive Y=North, Negative Y=South.`

`Piece = Negative/Positive, Negative/Positive, 0-3, 1-2, InstanceID`

The Piece lines have to do with the Preview Model used on the cursor, prior to building an item. It is only used for the preview, and the model itself is defined in the EffectsDirectory file. An actual IID has to actually be referenced here, whether it’s the correct IID or not, otherwise the preview model itself may not work properly. The \[CellLayout/Conslayout\] lines containing "\< ^" also have a bearing on the point of focus for the cursor and the Preview Model, in conjunction with this.

`PreviewEffect = preview_gh_av_straight_par`

The **PreviewEffect** lines reference string values found in the [EffectsDirectory](/effdir) file, which in turn references the [S3D](/s3d) file that is used for the semi-transparent preview of the interchange before you click the mouse button to plop it. Capital letters after the equals sign don’t seem to be valid, so be sure to use only lower case. Editing an Effects Directory file requires the use of a hex editor & knowledge of hex.

    CellLayout = ab.....
    CellLayout = cd.....
    CellLayout = cd+AB..
    CellLayout = ce+CD.<
    CellLayout = ce+CD..
    CellLayout = cd+EF..
    CellLayout = cd.....
    CellLayout = fg.....
    CellLayout = .^.....

The **CellLayout** lines show where the different types of tiles are located.

    CheckType  = a - groundhighway: 0x02040000,0xffff00ff check
    CheckType  = b - groundhighway: 0x02000004,0xffff00ff check
    CheckType  = c - groundhighway: 0x02040200 optional
    CheckType  = d - groundhighway: 0x02000204
    CheckType  = e - groundhighway: 0x02000204 optional
    CheckType  = f - groundhighway: 0x00040200,0x00ffffff check
    CheckType  = g - groundhighway: 0x00000204,0x00ffffff check
    CheckType  = A - avenue: 0x02040000,0xffff00ff check
    CheckType  = B - avenue: 0x02000004,0xffff00ff check
    CheckType  = C - avenue: 0x02040200
    CheckType  = D - avenue: 0x02000204
    CheckType  = E - avenue: 0x00040200,0x00ffffff check
    CheckType  = F - avenue: 0x00000204,0x00ffffff check

The **CheckType** lines do not have to correspond to any alphanumeric code; any capital or lowercase letter (and quite possibly other ascii characters) are recognized. For each CheckType line, there are two possible sections, one for each network type which crosses the tile (NOTE: only two network names possible per CheckType line). Each section has the following format:

`CheckType = X - networkname: RULFlagByte, check, optional, HexMask`

Items after the RULFlagByte can & do often appear in a different order. This is quite normal and can work. It’s generally best to stick to 'a' format though.

**RULFlagByte**

`0x02040000`

`02/04/00/00`

`South/East/North/West`

**check** makes the building engine check if the given network tile is in this position. If so, it must correspond to the RULFlagByte portion that the HexMask defines.

**optional** tells the building engine to not look for a S3D file for this interchange. Rather, it looks for a network tile of that network which corresponds to the RULFlagByte, and uses that S3D or [FSH](/fsh). If a tile of this network is there, it must correspond to the portion of the RULFlagByte that the HexMask defines.

**HexMask** tells the check and optional conditions which sides of the tile to look at. *FF* denotes that it must match, *00* denotes that it does not need to comply.

    ConsLayout = ......
    ConsLayout = |.....
    ConsLayout = |X....
    ConsLayout = .X||.<
    ConsLayout = .X||..
    ConsLayout = |X....
    ConsLayout = |.....
    ConsLayout = ^.....

The **'ConsLayout** lines work directly in conjunction with the CellLayout lines based on the CheckType lines make-up (such as SENW designation(s) for example). The ConsLayout lines also have a direct bearing on the S3D files and Terrain movements when placing the item. Various ASCII characters are valid on the ConsLayout, controlling how the S3D/terrain is affected. Note though, that some ASCII characters are not actually valid, & some set-ups (i.e. the use of certain characters & their formation) can render an item unable to plop.

- Note about ConsLayout & CellLayout: Be sure that the "^" and "\<" pointers are used and set properly for an item, for both the ConsLayout and CellLayout. These pointers basically call/reference the center (or point of focus) for the ConsLayout/CellLayout. If these little pointers aren't set properly, or point to an invalid item (such as a line item that is "optional"), then the item may be unable to plop.

`AutoTileBase = 0x0C883000`

This line is what tells the building engine where to start looking for all the sliced up tiles (the Exemplar & Path file(s). It references Exemplar & Path InstanceID which then references S3d files. The way it works is basically by placing a grid over the effected interchange. It finds the most top left tile in order to include all the (x) values and CheckType values which are not optional in the CellLayout, and defines that as this hex value. For each tile below it, the instance is incremented one value in the seventh digit. For each tile to the right of it, the instance is incremented one value in the sixth digit.

- **Note:** though the engine is capable of counting beyond 16 (0x#####FF0) tiles in either down and/or across directions for a single item, it is highly advisable to keep an item within a 16x16 tile size. Anything over this can cause problems.

An example diagram of how the AutoTilebase works, with n=starting point/Instance:

`Autopathbase = 0x12345000`

This function is optional. This item is almost exactly the same as the AutoTileBase function, and works in the same manner, a key difference with this function though is that it only references Path file(s), nothing else. In order to use this function, it should be placed just before the AutoTileBase function, otherwise it may not work properly. Also, the actual existence of path files (in the same range being called from the AutoTileBase function) *may* void this function. Generally, it isn’t used a great deal, but is quite useful when needed.

`PlaceQueryID = 0xA0000003`

This controls what the query tool shows when you have picked a specific interchange/junction type from the menu, and are trying to place the interchange/junction. This points to a Text based file IID. Note that these Text files may need to have their specific [Group ID](/group-id) in order for them to work properly.

`ConvertQueryID = 0xA0000000`

Basically controls what is displayed in the pop-up window that appears, for placing a given network junction/interchange. This only appears though when the Rules are triggered by using the network tools (and not a specific Menu Button for a given interchange/junction). This points to a Text based file by IID. Note that these Text files may need to have their specific Group ID in order for them to work properly.

`AutoPlace = 1`

This basically says, create the interchange/junction automatically when the Rules apply. However, the *ConvertQueryID* needs to be removed/commented out for the AutoPlace function to work effectively.

- A note about AutoPlace & ConvertQueryID functions: The rules/engine can often be rather picky about some rules, especially if there's more than one item with same/similar rules with either of these functions in place. If either of these two functions for an item don't seem to be working as they should, it is quite possible that the rules in place aren’t working as they should, contain errors, and/or another item in the RUL file is conflicting with it, which unfortunately does happen. Subsequently this means that only one of the items/set of rules may be able to call the function properly, in which case it may be better to have the item(s) manually placed or handled some how else.

`Costs = 400`

This affects the cost in the game. Depending on the make-up of the rules for an item, the actual cost displayed and charged to the budget may differ slightly than the Cost figure here in the RUL file. This is quite normal.

`[HighwayIntersectionInfo_0x00002016]`  
`CopyFrom = 0x2010`

- A note about CopyFrom: because of how the RUL file is loaded, the CopyFrom function for a given HighwayIntersectionInfo_value will only work if the copied value is lower than the current value for which the CopyFrom is for.

`Rotate = 3`  
  
`Transpose = 1`

These entries cover the other rotations. It copies the RUL from one instance and rotates clockwise 90 degrees \* the given number, or transposes the item, which basically flips all of the tiles in their orientation. Like many functions, the Rotate, CopyFrom and Transpose functions can be used together and are quite useful when needed.

- **Note:** While the Transpose & Rotate function can be used together under the same IntersectionInfo_Value section, and can be used to fix addtype lines auto resolve rotation issues, doing so has been known to be a cause of game-crashing upon entering the section in-game through rotating to the section.

`OneWayDir = #Number between 0-7#`

**One Way Direction** just says which direction the one way road is going.

`0 / 1 / 2 / 3 / 4 / 5 / 6 / 7`

`West / NorthWest / North / NorthEast / East / SouthEast / South / SouthWest`

## Others

Because of the loading order of the file, sometimes certain functions/rules may not work effectively/properly, whereas some functions can be used to advantage. An example of this is the AutoPlace = 1 rule; in some cases this will not work properly at all for an interchange, if the make-up of the interchange consists of checks that already exist previously in the files (see note above regarding AutoPlace/ConveryQueryID). Some other examples of this can be seen in the RUL file itself.

### Bulldoze Cost

Unfortunately, the Intersection Ordering RUL file was originally geared and made with (Elevated) Highways in mind (or as the focal point). Because of this, the bulldoze cost of anything made/created out of this file will typically be the same as if everything were Highways.
