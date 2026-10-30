---
title: "RUL0"
description: ""
published: true
date: '2021-02-19T10:55:42Z'
tags: ["NAM", "RUL Files", "Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2019-08-09T22:35:27Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">RUL0</th></tr>
<tr><td><strong>Name</strong></td><td>Intersection Ordering RUL</td></tr>
<tr><td><strong>Format</strong></td><td><a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x0A5BCF4B</td></tr>
<tr><td><strong>Group</strong></td><td>0xAA5BCF57</td></tr>
<tr><td><strong>Instance</strong></td><td>0x10000000</td></tr>
<tr><td><strong>Comments</strong></td><td><em>See also: </em></td></tr>
</table>
</div>

**RUL 0x10000000**, also known as the **Intersection Ordering RUL** and **RUL0**, is a [RUL File](/rul-file) which defines Interchanges and [Puzzle Pieces](/puzzle-piece) and their placement into **TAB Loops** under a certain menu button. There are two different sections to this file, the first of which defines TAB Loops and Rotation Rings, the second of which defines the Puzzle Pieces and relates them to those Rotation Rings. The [Network Addon Mod](/network-addon-mod) (NAM) relies on an extensive series of modifications to this file, crucial to its functionality. It is placed in the NetworkAddonMod_Controller.dat file. The original Maxis file can be found in SimCity_1.dat.

Only one copy of this file can be loaded by the game at one time, so which ever one is last in alphabetical order in the Plugins will be loaded by the game. The [Red Arrow Bug](/red-arrow-bug) is caused by having transit mods with menu buttons that are not defined in the loaded version of RUL 0x10000000.

It is important to note, before one starts editing this file, that it contains many intricately interconnected parts, and any modifications, no matter how simple, may have widespread effects, including crashing the game. It is also entirely possible for a section to be set up correctly, and still not behave effectively or as expected in-game due to conflicts with another, also correctly done, part of the file. This may be due to loading order, conflicting rules, properties that don't work together as expected, and any number of other problems. Sometimes this may work to your benefit, other times it may not.

## TAB Loop Section

### Basic Syntax

The TAB Loops section of RUL 0x10000000 has a relatively basic syntax, and it consists of a series of lines of code known as **Rotation Rings**, which reference Puzzle Pieces and their rotations and mirrors by an internal, RUL-specific series of reference numbers, known as *IntersectionInfo IDs* (hex-id's).

The [Maxis](/maxis) comments from within the file itself are:

    ; RotationRing = hex-id [,hex-id...]
    ;
    ;   Creates a ring of rules that are cycled through via
    ;   Home/End or automatically by the tool as it tries to
    ;   auto-fit rules to the current mouse point.
    ;
    ; AddTypes = hex-id [,hex-id...]
    ;
    ;   Attaches another ring to the last ring, creating type
    ;   rings perpendicular to the rotation ring.  Type rings
    ;   can be cycled through via Tab/Shift-Tab.  Generally,
    ;   type rings are set up to preserve rotation as you
    ;   cycle through rules of different network types.
    ;
    ; A given rule can only belong to ONE rotation ring and
    ; ONE type ring.  Attempting to hook a rule into more than
    ; one rotation or type ring will result in the rings getting
    ; trashed.

The first line of any TAB Loop will always begin with a "RotationRing =" reference, which defines the start of the loop. Consider the following example taken from the [RHW](/rural-highway-mod) Puzzle Piece TAB Loop:

    RotationRing = 5000, 5001, 5002, 5003, 5004, 5005, 5006, 5007 ;RHW-4 Starter Piece

Further Rotation Rings are defined by using the "AddTypes =" reference:

    AddTypes = 5010, 5014, 5011, 5015, 5012, 5016, 5013, 5017 ;RHW-4/MIS-1 Ramp A
    AddTypes = 5020, 5024, 5021, 5025, 5022, 5026, 5023, 5027 ;RHW-4/MIS-1 Ramp B

Essentially, all of the rotations of a given intersection type (i.e. cloverleaf) for a particular set of intersecting networks are put on a single line, in clockwise order. The different combinations of intersecting network types (i.e. elevated highway/ground highway, elevated highway/avenue, etc.) are placed on successive lines so that you can tab through the network types (moving from one line to the next), or home/end through the rotations (moving along a line). The IntersectionInfo IDs are the last four digits of an [Instance ID](/instance-id) for that particular interchange.

The user experience of this part of the RUL0 File in-game is that when you click on a particular menu button, you are presented with the first item in the *RotationRing* line. How you move through the particular TAB Loop depends on what buttons you press next:

- Pressing "Home" will show you the next item on the same line.
- Pressing "Tab" will show you the first item on the next line.

Once the end of the line is reached, you are returned to the beginning of the line. Once the last line is reached, you are returned to the first line. Of course, pressing "End" moves you backwards through whatever line you are in, and pressing "Shift + Tab" moves you to the previous line in the loop.

The difference between *RotationRing* and *AddTypes* lines is that *RotationRing* is used to define the start of a section, or button, whereas *AddTypes* is used for the successive items attached to that *RotationRing*. So, having only one *RotationRing* and 10 *AddTypes* following it below is perfectly normal.

The length of the RotationRing and AddTypes entries can vary quite dramatically, with some Maxis items only containing 2 entries, while the NAM One-Way Road puzzle pieces contain 32 IntersectionInfo IDs per line. The length of these lines (number of entries per line) must be kept consistent under a single TAB Loop. Otherwise, serious stability issues can result when using the TAB Loop, including missing and duplicate pieces and rotations, and in some cases, [CTDs](/ctd).

While TAB Loops were initially only used for highway interchanges, they have been massively expanded by NAM to include the wide array of puzzle pieces made available by that mod. Consequently, while this specification will often refer to parts of the file as applied to highway interchanges, it is far from the only way these are used. The [NAM Team](/nam-team) has a set of guidelines for the placement of items within TAB Loops, in which the IntersectionInfo ID should begin with a specific digit depending on the primary network for the puzzle piece.

IntersectionInfo ID references cannot be duplicated. For instance, once 5001 is used once as part of the RHW-4 Starter Piece Rotation Ring, it cannot be used in any other Rotation Ring. Otherwise, there will be flaws in the Rotation Rings referencing that ID, preventing them from functioning properly.

### Relationship of Rotation Rings to Menu Icons

The menu button allowing access to the TAB Loop and its Rotation Rings consists of a [PNG](/png) file showing the icon in its four states (as is the case with Lots), and an [Exemplar](/exemplar) (GID 0x2A3858E4) referencing the Rotation Ring. Two [LTEXT](/ltext) files, one with a short description (GID 0x123006BB) and a long description (GID 0x123006AA), are also important to have. The IID for all of these files will always begin with "6A47", and the last four digits will correspond to the first IntersectionInfo ID (hex-ID) reference in the first Rotation Ring. For the example shown above, the IID for the RHW Puzzle Piece Menu Button would be 0x6A475000.

## Intersection Tile Types Section

This is a very small part of the file, and simply contains a list of *DefineType* entries for each of the transit networks. For example,

    DefineType  = 0x00000000,Road
    DefineType  = 0x00000002,Highway

The only two types defined originally were 0 and 2 as shown above, however the list has been expanded by NAM to include the other transit networks. The purpose of this section is not known (?really?), and it appears to be a backup system used by Maxis prior to [Rush Hour](/rush-hour) that is obsolete at the present for defining intersection types. Modifying the values here has no effect on building intersections in game. It has also been noted that the entire section can be commented out without causing any known effects on the game.

Another theory holds that this section defines types to be used later on in the CheckType sections of Puzzle Piece layouts (see Layout Section below).

## Intersection Info Section

The **Intersection Info Section** of RUL 0x10000000 is the section that defines the actual Puzzle Pieces. There are three main sections to an IntersectionInfo ID entry. Please keep in mind that within each of these sections, the lines in that section can come in any order. The general progression is similar, but some things are moved around in different interchange definitions. However, it does not change how they are loaded in memory. Consequently, not every section will exactly follow the format prescribed below, however, all of the necessary parts must still be within the section somewhere. It should also be noted that while Maxis did provide comments on this section in the file, many of them have been found to be obsolete following major revisions to the file format caused by Rush Hour, and consequently are dealt with here only where they add some special information to the specification.

### Header

The **Header** generally gives a description of the piece in question, info pertaining to the date of creation and the creator of the piece, and references the [Preview Model](/preview-model) and [EFFDIR](/effdir) for the item. For example:

    [HighwayIntersectionInfo_0x00009200]
    ;Added by Tropod 06.08.04
    ;avenue orthogonal x groundhighway orthogonal puzzle piece
    Piece = -16.0, 0.0, 0, 0, 0x54262400
    PreviewEffect = preview_aven_puzzlepiece008

The first line contains the Intersection Info reference that is used by the Rotation Rings in the TAB Loop Section. The format of this line is:

    [HighwayIntersectionInfo_InstanceID]

The text before the IID must remain as "HighwayIntersectionInfo\_" regardless of the network type(s) actually involved, or else the RUL will not be recognized. This is one example of carryover from when these RULs only applied to highway interchanges.

Each interchange/overpass/junction/etc., must have a unique IID, otherwise conflicts will arise, and some/all of the rules with the same IID will not work. The Instance IDs typically have zeros in the first four digits to allow use in the TAB Loops, which only reference the last four digits of the IID (as the IntersectionInfo ID). While this is not strictly necessary for items not included in the TAB Loops, the same convention is often followed for convenience. An example of an item not in a TAB Loop would be an intersection that is always automatically created and cannot be plopped. Note also that NAM uses its own specific format for these IIDs, which can differ from the Maxis standard.

The second and third lines of the header show the creator, date of creation, and a general description of the piece to which the entry pertains. These lines are commented out by a semi-colon (;) and are not read by the game (hence, they are technically optional).

The fourth line, beginning with "Piece =" partially defines the Preview Model, more on this below.

The fifth line, **PreviewEffect**, references the alphanumeric name for the Preview Model, which is a string specified in the associated [EFFDIR](/effdir) file. The EFFDIR entry in turn references the [S3D](/s3d) file that is used for the semi-transparent preview of the interchange before you click the mouse button to plop it. Capital letters after the equals sign don’t seem to be valid, so be sure to use only lower case.

#### Piece

The **Piece** lines are real oddballs. They predate Rush Hour, and have been rendered partially useless. Prior to Rush Hour, an intersection preview was made using a single ploppable piece. Since Rush hour, that has been changed so that the effect directory (EFFDIR) makes the preview. However this line is still absolutely necessary for the game to build the intersection, and commenting one out will crash the game.

An example Piece line is repeated here for reference:

    Piece = -16.0, 0.0, 0, 0, 0x54262400

The format of this line is:

    Piece = X-offsest, Y-offset, Rotation, Flip, PreviewIID

The first two values of the Piece line control the position of the cursor when placing the intersection, relative to the preview of the intersection. This does not affect the actual plopping position though. The first is how deep to the left (or E/W direction), from the right side of the intersection on cell layout, the cursor should be in the form of a value with one decimal. Positive values are east, and negative values west. The second is where relative to the top or bottom on the cell layout (or N/S direction) the cursor should be from the vertical center. Positive values are north, and negative south.

The 3rd is a rotation key for the preview, setting it to 0 implies no rotation, setting it to 1 will turn the preview of the intersection by 90 degrees, and so forth for setting it to 2 and 3.

The 4th is a sort of preview flip (or mirror) key. Setting it to 1 instead of 0 will make it so that if you were to build a T-intersection on one side of a highway, with the face pointing down, hovering the intersection on that side of the highway would now show it as pointing up on the z-axis instead. It has no effect on the actual plop however.

The 5th value contains the pre-Rush Hour Instance ID for the entire intersection to use as a preview. An actual IID has to actually be referenced here, whether it's the correct IID or not, otherwise the preview model itself may not work properly.

The CellLayout/ConsLayout lines in the Layout Section containing "\< ^" also have a bearing on the point of focus for the cursor and the Preview Model, in conjunction with the Piece line.

### Layout Section

The **Layout** portion defines where the Puzzle Piece Models are placed, the fundamental layout of the piece according to basic network pieces, any draggable stub handles, and the slope orientation of the puzzle piece. It typically consists of three subsections, the **CellLayout**, **CheckType**, and **ConsLayout**, as well as the **AutoTileBase** property, as shown below.

    CellLayout =........... 
    CellLayout =....WX....< 
    CellLayout =....YZ..... 
    CellLayout =.....^..... 

    CheckType = W - groundhighway: 0x02040200 avenue: 0x04020002 
    CheckType = X - groundhighway: 0x02000204 avenue: 0x04020002 
    CheckType = Y - groundhighway: 0x02040200 avenue: 0x00020402 
    CheckType = Z - groundhighway: 0x02000204 avenue: 0x00020402 

    ConsLayout =........... 
    ConsLayout =....++....< 
    ConsLayout =....++..... 
    ConsLayout =.....^..... 

    AutoTileBase=   0x54262300

The arrows (\< and ^) on both the CellLayout and ConsLayout define the "cursor position" when placing the piece (which, in this example, is on the tile marked "X" in CellLayout). It must be the in the same location in both sections, or else there will be unpredictable results.

#### CellLayout and AutoTileBase

The **CellLayout** subsection defines the layout and design of the puzzle piece, telling the game where to look for and place the individual models that make up each puzzle piece. Generally speaking, the "top-left" corner of this layout corresponds to the "lowest" IID used in the puzzle piece, which is defined in the **AutoTileBase** line, at the end of the Layout Section. The game automatically generates a grid of IIDs based upon the AutoTileBase value.

In the example above, the tile in the CellLayout marked "W" is the "top-left" tile, and corresponds to 0x54262300 (the AutoTileBase IID). The game determines horizontal and vertical positioning of the other individual single-tile models forming the puzzle piece based upon the AutoTileBase IID, with pieces to the right having IIDs increasing by 100 per tile (incrementing the 6th digit), and pieces below it increasing by 10 per tile (incrementing the 7th digit). Thus, the piece marked "X" will have an IID of 0x54262400 (1 tile to the right), "Y" will have an IID of 0x54262310 (1 tile below), and "Z" will have an IID of 0x54262410 (1 tile to the right and 1 tile below).

- **Note:** Though the game engine is capable of counting beyond 16 (0x#####FF0) tiles in either down and/or across directions for a single item, it is highly advisable to keep an item within a 16x16 tile size. Anything over this can cause problems.

This relationship of the IID's is shown below in grid format. The "AutoTileBase" tile is shown in **bold**.

<table>

<tr>

<th>

0x54262300

</th>

<td>

0x54262400

</td>

</tr>

<tr>

<td>

0x54262310

</td>

<td>

0x54262410

</td>

</tr>

</table>

The IID's referenced here are for [Exemplar](/exemplar) and [SC4Path](/sc4path) files, which then point towards the [S3D](/s3d) files of the actual model.

As for that actual grid of letters and punctuation that makes up the CellLayout subsection, what that shows is where different types of tiles are located. Contrary to the included comments from Maxis, there are only four predefined values for the CellLayout:

- The carrots (^,\<) which define what the center tile is and where your mouse will be, so that the preview can be aligned with the intersection when it's plopped.
- Periods (.) which tell the building engine to not look for a tile to plop in that position.
- Plus signs (+) which tell the building engine to look for a tile to place there, but the tile is a non-standard road tile, because it has no tile side rules. This is true for the actual ramps between road/highway and highway/highway. These tiles also do not show up in the CheckTypes section below.

Everything else in there is completely arbitrary, though convention holds that when the same piece is repeated within the layout, the same character should be used for it in every location, unless there is a specific reason not to do so. Also note that the characters used here are related to the CheckType subsection that follows, and consequently the same character *cannot* be used for different types of tiles.

#### CheckTypes

The **CheckTypes** specify an underlying network configuration that lies below the piece. The CheckType has an effect on piece placement, and if set up properly, can allow for "auto-resolving", a useful feature which allows for a user to plop a piece directly over a base draggable network. The letters in the CellLayout ("X" in the format spec below) correspond with the same letters in the CheckType section. It is also possible to define tiles in CellLayout that do not relate to the CheckTypes, by specifying "+".

CheckType lines have the following format:

    CheckType = X - networkname: RULFlagByte, HexMask check optional

Items after the *RULFlagByte* are optional, and the items in a CheckType line don't always appear in the order shown above.

- *RULFlagByte* follows the same system of two digit South-East-North-West (0xSSEENNWW) [Network Flags](/network-flags) as is used in [RUL 0x10000001](/rul1) and the [Individual Network RULs](/individual-network-ruls).
- *check* makes the game engine check if the specified network tile already exists in this position. If so, it must correspond to the RULFlagByte portion that the HexMask defines. Tile definitions in CheckTypes with "check" tags at the end are not counted in the IID grid, and instead create stubs for connecting the puzzle piece to surrounding draggable networks.
- *optional* tells the game engine to not look for a S3D file for this tile of the interchange. Rather, it looks for a network tile of the specified network which corresponds to the RULFlagByte, and uses that S3D or FSH. If a tile of this network already exists there, it must correspond to the portion of the RULFlagByte that the HexMask defines.
- *HexMask* tells the *check* and *optional* conditions which sides of the tile to check against the RULFlagByte. *"ff"* denotes that it must match, *"00"* denotes that it does not need to comply. "00" indicates a direction that the stub cannot be connected, while "ff" indicates a direction that a stub can be connected.

CheckType lines must include a set of values for each network that crosses that particular tile. For example, where only one network crosses the tile (in this case a highway), you can have:

    CheckType = e - highway:0x02040000,0xffff00ff check

Which shows the use of the HexMask and *check* properties.

Whereas if two networks cross the tile (in this case a highway and an avenue), you can have:

    CheckType = A - highway: 0x02040200 avenue: 0x04020002

In this case all you have are the networkname and RULFlagByte properties for each network.

#### ConsLayout

The **ConsLayout** section, short for "Construction Layout", controls how the terrain is affected when the piece is placed, in conjunction with either the default Maxis slope properties, or whatever [Slope Mod](/slope-mod) the user may have installed. Basically, it is there to modify the terrain to make sure the intersection plops properly. In more technical terms, it relates to the [Network Tuning Exemplars](/network-tuning-exemplars). There are several different symbolic flags used here:

    |, - : Orthogonal
    /, \ : Diagonal
    #    : Intersection (Orthogonal)
    X    : Intersection (Diagonal)
    +    : Special - Matches terrain according to neighboring tiles, loosely "match existing slope."
           Can cause "sinkhole-to-China" bugs if used improperly.
    .    : Similar to CellLayout, tells the game not to check or modify terrain here.
    ^, < : Same as CellLayout, define the center of the piece. Must match the same location used in CellLayout.

While the ConsLayout is fairly flexible in terms of what you put into it, at times, if it is set in certain ways, it can prevent the puzzle piece from being placed in-game, even on perfectly flat terrain. Note that other characters than those listed above may be used, however their use is rare.

The -,\|,/,and \\ represent the various angles of the road to correct the terrain for, the \#'s are for the center of the intersection or the base, which must all be on the correct terrain to look good, and the X's are for on-ramps, which if not present will have the onramps on wierd angles on hilly terrain.

### Definition Section

The **Definition** section is the final part of an IntersectionInfo ID entry, and contains various items that provide additional information about the puzzle piece or interchange being defined in the previous two sections of the entry. The properties that may be included in a Definition section are shown below as an example. Note that it is common for only some of these properties to be present. Additionally, some of these are only used on Maxis items, and have essentially been deprecated.

    AutoPathBase = 0x12345000
    AutoTileBase = 0x54262300
    ReplacementIntersection = 0, 0
    PlaceQueryID = 0xB0009055
    Costs = 1000
    ConvertQueryID = 0xB000E820
    AutoPlace = 1
    HandleOffset = 2,0
    StepOffsets = -6, 6
    OneWayDir = 4

As you can see in that example, *AutoTileBase* may be considered part of the Definition section. However, since it relates to the layout of the tiles in the interchange, it is described in the Layout section above. Either way, it is always there, and always in the same spot, whether you consider that the end of the Layout section or beginning of the Definition section. If *AutoPathBase* is present, it comes before AutoTileBase.

There are several properties contained in this section, and they are defined below:

- *AutoPathBase* specifies the path for the "top-left" tile in the layout, generally when the IID of the desired path differs from the AutoTileBase IID. This item is almost exactly the same as the AutoTileBase function, and works in the same manner, a key difference with this function though is that it only references Path file(s), nothing else. This is typically used to "copy" a path or a set of paths from another puzzle piece, as is the case with some of the Pedestrian Mall puzzle pieces. This function is optional. In order to use this function, it should be placed just before the AutoTileBase function, otherwise it may not work properly. Also, the actual existence of path files in the range being called from the AutoTileBase function may void this function. Generally, it isn’t used a great deal, but is quite useful when needed.
- *AutoTileBase* is defined in the Layout section above.
- *ReplacementIntersection* is generally not used. The ReplacementIntersection line takes an intersection and rotates and flips it to create another intersection as needed, with the first value being the rotation and the second being the flip. The purpose of this property is not known, and Maxis themselves appear to never use it, always providing the value 0,0.
- *PlaceQueryID* references the IID of the LTEXT file that will show when the puzzle piece is being hovered. This controls what the query tool shows when you have picked a specific interchange/junction type from the menu, and are trying to place the interchange/junction. Note that these LTEXT files may need to have a specific Group ID in order for them to work properly.
- *Costs* defines the cost of placing the item in game, in [Simoleons](/simoleon). It is the cost that appears in the menu, as well as the cost to build the intersection assuming all needed pieces minus the intersection itself are already in place. The price increases substantially for each required piece not already in place or when the intersection piece is not being built on flat land. The bulldoze cost, however, is always set, based upon the costs of the Maxis Highway network, regardless of the network types actually specified in the CheckTypes. Depending on the make-up of the rules for an item, the actual cost displayed and the cost charged to the budget may differ slightly from the Cost figure listed here in the RUL file. This is quite normal.
- *ConvertQueryID* references the IID of LTEXT files relating to the optional auto-placement of puzzle pieces, as is done with the Elevated Highway-to-Ground Highway transition piece in the NAM. Basically controls what is displayed in the pop-up window that appears, for placing a given network junction/interchange. This only appears though when the Rules are triggered by using the network tools, and not a specific Menu Button for a given interchange/junction. Note that these LTEXT files may need to have a specific Group ID in order for them to work properly.
- *AutoPlace* basically says to create the interchange/junction automatically when the Rules apply. However, the ConvertQueryID needs to be removed/commented out for the AutoPlace function to work effectively.

A **note about AutoPlace and ConvertQueryID functions**: The rules/engine can often be rather picky about some rules, especially if there is more than one item with same/similar rules with either of these functions in place. If either of these two functions for an item don't seem to be working as they should, it is quite possible that the rules in place aren't working as they should, contain errors, and/or another item in the RUL file is conflicting with it, which unfortunately does happen. Subsequently this means that only one of the items/set of rules may be able to call the function properly, in which case it may be better to have the item(s) manually placed or handled in some other way.

- *HandleOffset* specifies the place to build the intersection relative to where you're hovering. Both values can be any number that can fit on the map from your position both positive or negative. The first value is the distance straight out from your cursor in a line the intersection will build at, either x or z. The second value is the distance to the side that the intersection will build at, once you have reached the destination specified by the first value. For example, you can have an intersection build 20 tiles out, and 15 to the side of where you are trying to plop. It is not generally used.
- *StepOffsets* sets parameters for dragging that must be achieved before the intersection can be considered valid. The second value is how far from the intersection you must continue dragging until it is valid, the bigger the number, the further from the intersection you must drag. The first value controls the start offset or where you should be dragging from to make it a legal intersection, however it doesn't seem to work, and changing the value to a high negative, a positive, or a 0 has had no effect on the starting drag point necessary in any testing that has been performed. An effect similar to this can be seen when placing highway interchanges, in that it is generally not possible to place multiple interchanges in the same travel direction adjacent to each other, as well as the condition where the highway needs to continue so many tiles past an intersecting road to place an interchange at the intersection. The mechanics of how these relate to each other is not well known or documented however. Note also that this property is sometimes located at the end of the Header section of the entry, before the Layout section.
- *OneWayDir* specifies the direction the one way road is going out of the 8 possible radiating directions where a highway is in an intersection with a one way road. Possible values are 0 to 7, with 0 being West, and continuing clockwise to 7 being Southwest. The use of this function is also not well documented.

### Rotation Section

The **Rotation Section** allows one to take a full Layout and transform by rotating and mirroring it in various ways without requiring a new Layout, and also, to fill out Rotation Rings with Rotation Clones. It fully replaces the Layout and Definition sections of the entry. A typical IntersectionInfo ID entry with a Rotation section may look like:

    [HighwayIntersectionInfo_0x00009A18]
    ;comments as desired
    CopyFrom = 0x9A10
    PlaceQueryID = 0x5CE42101
    Transpose = 1
    Rotate = 1

Note that the first line of the Header section, the *HighwayIntersectionInfo_IID* part, is still required when using a Rotation section, since this is essentially a definition of an entirely new interchange. It simply copies all of its properties from some previously defined interchange.

The following properties are valid in a Rotation section:

- *CopyFrom* basically specifies another *IntersectionInfo ID* to copy the Layout, Preview Model, etc. from. Because of how the RUL file is loaded, the CopyFrom function must specify an IID that is lower than that of the current entry.
- *PlaceQueryID* works the same as in the Definition section of a normal entry, and simply replaces the LTEXT of the item being copied with a new LTEXT specifically for this interchange. The command must be placed under the *CopyFrom* command, but before any transformation commands.
- *Rotate* rotates the puzzle pieces clockwise in 90 degree segments. The resulting rotation is 90 \* (value), valid values are 0 to 3.
- *Transpose* is essentially a mirror command. It does not work on pieces using [False Intersections](/false-intersection), such as starter pieces for [Override Networks](/override-network). Possible values are 0 or 1, 0=no flip, 1=flipped.

**Note:** While the Transpose and Rotate functions can be used together, this is not done in practice since any rotations which require both are simply transformed from an interchange which has already been rotated. Using the two together in the same entry has also been known to crash the game upon entering the section in-game through rotating to the section.

1.  [Network Specs](/network-specs)
