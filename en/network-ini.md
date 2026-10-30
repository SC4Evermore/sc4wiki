---
title: "Network INI"
description: ""
published: true
date: '2019-08-09T02:55:13Z'
tags: ["File Formats/SC4", "Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2008-08-31T11:05:02Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Network INI</th></tr>
<tr><td><strong>Name</strong></td><td>Intersection Ordering RUL</td></tr>
<tr><td><strong>Format</strong></td><td>Network INI/<a href="/rul-file">RUL File</a></td></tr>
<tr><td><strong>Type</strong></td><td>0x00000000</td></tr>
<tr><td><strong>Group</strong></td><td>0x8A5971C5</td></tr>
<tr><td><strong>Instance</strong></td><td>0x8A5993B9</td></tr>
<tr><td><strong>Comments</strong></td><td><em>See also: </em></td></tr>
</table>
</div>

The **Network INI** is a file which handles a number of different functions related to the game's transit and utility networks. While technically a different file type, as evidenced by its [Type ID](/type-id), it bears some resemblance to the [RUL Files](/rul-file).

## History

Prior to the [Rush Hour](/rush-hour) expansion in 2004, the Network INI carried all of the game's network RUL code. With Rush Hour and the expansion of the transit network systems it entailed, [Maxis](/maxis) decided to modularize some of the more common and intensive operations into separate RUL files, leaving the more specialized functions in the INI. Theoretically, code from the post-Rush Hour RUL files can still be run from the INI. While "Network INI" is the accepted name for the file currently, it has also been known as the **Remapping** file historically due to that being in the names of many of the sections.

## Sections

The Network INI file is divided into nine separate sections, each handling a certain type of functionality. All bridge exemplars are considered a single section for the sake of argument and since they hold the same structure.

### Debug Rules

The **DebugRules** section contains three debug settings (as the name entails) that Maxis used during testing. Changing the values now has no effect. The default value for each setting is zero *(0)*.

    [DebugRules]
    Reload=0
    Trace=0
    Debug=0

### UK Path Remapping

This section handles [Left Hand Drive](/left-hand-drive) (LHD) conversion for certain networks and pieces; namely rail-type networks. Basically, this section is used to replace particular path files, or sets of path files, at run-time for any given in-game tiles. The Maxis description of the section, given in the file itself is:

    ; In locales that have drive-on-left as default, the path system reverses
    ; all path directions from the stored points.  This handles all cases
    ; except the one-ways, which must remain consistent with the one-way flags
    ; stored in the occupants.  The normal one-way tiles are designed to be
    ; bidirectional and are handled correctly by the auto-flip code, but some
    ; of the intersections have pre-baked one-way paths that are incorrectly
    ; flipped.  We have explicit forward and reverse versions of those, so
    ; what we do here is swap the two versions for drive-on-left so that the
    ; reversal code re-flips the one-way paths back to their correct
    ; orientation.
    ;
    ; Format:
    ;
    ;    <anything> = <match-id>, <match-mask>, <new-id>, <add-mask>
    ;
    ;   match-id:   value to look for after masking
    ;   match-mask: AND mask to eliminate dont-care bits from the match
    ;   new-id:     base for new texture ID on a match
    ;   add-mask:   bits from original ID to add to new-id

It should be noted that while Maxis says this section handles "all cases", what they mean is that it handles all *car* cases. Other types of transportation are not affected by this section.

Reading the notes that [Tropod](/people/tropod) and other modders have written into the NAM's Network INI will explain further about minor quirks and [NAM](/nam) conventions regarding this section.

An example line from this section looks like this:

    1   = 0x03000000,0xFF000000,0x43000000,0x00FFFFFF

The value on the left side of the equal (=) sign can be anything, but by convention it is a number counting up for each subsection of code. The first value to the right of the equal sign is the source [Instance ID](/instance-id) (IID). This, in conjunction with the second value, tells the game which IIDs this line affects. This is calculated with a [bitwise AND](http://en.wikipedia.org/wiki/Bitwise_AND#AND). Therefore, this line only applies to path files with an IID starting with 0x03. The rest of the digits can be any value, since all the game cares about is the first two digits. The second value is the mask that filters out the important digits of the IID from the others - digits with an *"F"* are selected by the mask, while digits with a *"0"* are ignored.

The third and fourth values are the target IID and corresponding mask. This time, the bitwise AND is used by the game to determine which digits of the target IID are insignificant and are to be replaced with the source IID's values.

In summary, the example line above says that any Path files with IDs of *0x03######* be replaced with the Path files that exist in *0x43######*, for Left Hand Drive games. The step by step process for a specific individual file is:

1.  Game in LHD mode loads up path *0x03001400*.  
2.  Game loads Network INI and finds this section to determine how paths should be replaced.  
3.  Game evaluates a line by taking the bitwise AND of the first value and the second, and also a bitwise AND of the path-in-question IID and the second value in this line.  
    \*If the two are equal, do a bitwise AND on the path-in-question and do another one on value three and the inverse of value four. Add the two results to get the final IID. Finish.  
    \*If the two are not equal, evaluate the next line. If the end of the section is reached, the path file is not replaced.  

Note that comments can be appended onto the end of these lines using a semicolon, for example:

    1   = 0x03000000,0xFF000000,0x43000000,0x00FFFFFF ;rail ~ also contains some custom paths

### Texture Remapping

The texture remapping section handles special preview textures for draggable networks (namely, what you see before you release the mouse button). Normally, when a network is dragged, the texture that you see is the texture that will be placed, disregarding [wealth](/wealth). If there are models that will be placed on a tile, then the game will look for a [texture](/texture) at the same IID as the [Model Exemplar](/model-exemplar). If no texture is found in either case (network texture or model exemplar), then an orange-brown square is drawn.

There are issues with using textures at the same IID as the model, usually with wealthing. To avoid this, preview textures can be remapped, which is what this section does. Maxis uses it to provide previews for ground highways and elevated highways.

The syntax for this section is as follows:

    <anything> = <source IID>, <mask>, <target IID>, <mask>, <OPTIONAL: rotation>, <OPTIONAL: flip>

The masking method used here is the same one used by UK Path Remapping (see above). Rotation and flip rotate and flip the texture, and are optional. If one is to be used, the other must also be specified.

The NAM uses this section to provide preview textures for ERHW-4 and E-STR, as well as custom maxis highway pieces such as tight "S" bends.

### Shadow Remapping

Shadows for networks in [SimCity 4](/simcity-4) are handled in three ways:

1.  Using the Shadow Remapping section in the Network INI,
2.  Using the Shadow Edge Remapping section in the Network INI, and
3.  Providing a shadow texture at the same IID as the item.

These are evaluated in order.

The Maxis comments on this section from within the file are:

    ; Many of the shadows in the network system have similar or identical graphics.
    ; This section provides a general mechanism for remapping shadow textures, using
    ; entries of the form:
    ;
    ; <anything> = <match-id>, <match-mask>, <new-id>, <add-mask> [, <rotation>] [, <flip>] [, <continue>] [, <submask>]
    ;
    ;   match-id:   value to look for after masking
    ;   match-mask: AND mask to eliminate dont-care bits from the match
    ;   new-id:     base for new texture ID on a match
    ;   add-mask:   bits from original ID to add to new-id
    ;   sub-mask:   bits from original ID to subtract from new-id
    ;   rotation:   rotation to apply to remapped texture before applying tile rot/flip
    ;   flip:       flip to apply to remapped texture before applying tile rot/flip
    ;   continue:   if '1', continue processing rules after this one
    ;
    ; For instance, if we wanted to map textures 12340000 through 1234000F to
    ; 00010000:0001000F:
    ;
    ;   dummy = 0x12340000, 0xFFFFFFF0, 0x00010000, 0x0000000F
    ;
    ; Or, to map all zoom 2 and 3 textures to zoom 1:
    ;
    ;   z2to1 = 0x00000001, 0x0000000F, 0x00000000, 0xFFFFFFF0
    ;   z3to1 = 0x00000002, 0x0000000F, 0x00000000, 0xFFFFFFF0
    ;
    ; Higher entries have precedence.

The format used here is extremely similar to the Texture Remapping section. The differences are the addition of the *submask* attribute, which is usually unused anyways; and the *Continue* attribute. The *submask* is bits from the original result IIDs of the search that you don't want added to the new IIDs. *Continue* is always implied to be 0 unless otherwise specified. If 1, the new-ID is used as match-ID in subsequent entries. This can be iterated. If 0, the new-ID is returned, no matter if it matches subsequent entries. Maxis' final comment regards the line number of a line. Because lines are evaluated sequentially, a line at the very top of the section will override a line below it that has the same IID match.

An example using all eight attributes is:

    intx_diagcloverface = 0x0C006600, 0xFFFFFE00, 0x0C006A00, 0x000000FF, 0, 1, 1, 0x00000F00

This section is ended by the line

    default = 0,0,0,0  ;use edge remapping for all other shadows

which passes off all non-matched remaps onto the next section.

### Shadow Edge Remapping

This section handles remapping by checking [Network Flags](/network-flags).

The Maxis comments on this section from within the file are:

    ; For certain pieces in complex intersection models it is inconvenient
    ; to map shadows by piece IDs, particularly those on diagonals.
    ; Here we map pieces to shadows by edge flags instead:
    ;
    ;   <anything> = <network-type>, <edge-conditions>, <new-texid>, <add-mask> [,<rotation>] [,<flip>]
    ;
    ;   network-type:       'highway', 'lightrail', etc.
    ;   edge-conditions:    32-bit edge mask (0xbbrrttll)
    ;   new-texid:      base texture ID for new shadow
    ;   add-mask:       bits from piece ID to add to base texture ID
    ;   rotation:       pre-rotation to apply to new shadow
    ;   flip:           pre-flip to apply to new shadow
    ;
    ; The edge remapping table is used whenever the rule entry in the
    ; regular shadow table has a <new-mask> of 0.

*Edge-conditions* refers to the Network Flags for the tile. Note that it uses the same SSEENNWW format used by [RUL 0x10000000](/rul-0x10000000) (RUL0) and [RUL 0x10000001](/rul-0x10000001) (RUL1).

This section is unusual in that it does not use the hexadecimal prefix *0x* in its values.

An example line:

    histraight = highway,  04020002, 02001500, 0000000F, 0, 0

### PowerPoles

This section defines the appropriate power pole model to display depending on which sides of the tile the pole must connect to power lines. Knowing the sides that must be connected, one can find the appropriate BitFlag (see below), and the corresponding power pole exemplar for that condition. The exemplar, in turn, points to the power pole model.

The Maxis comments on this section from within the file are:

    ; This section lists the different power pole models present and indicates the connection
    ; directions supported by those models. The supported directions are represented using a 4-bit
    ; flag. Bit0  (LSB) is set to 1 if the pole supports connection in direction 0, Bit1 is set to
    ; 1 if the pole supports connection in direction 1 and so on..
    ;
    ;    |------>x
    ;    |
    ;    |
    ;    \/
    ;    z
    ; direction 0 : parallel to x axis
    ; direction 1 : line connecting (-k, -k) to (k, k)
    ; direction 2 : parallel to z axis
    ; direction 3 : line connecting (-k, k) to (k, -k)

The four directions define the two axial (0 and 2) directions across the tile, and the two diagonal (1 and 3) directions across the tile.

The actual format of the entries is such:

    Bitflag=ModelResource

With the two values defined as:

- ModelResourse: An Instance ID for an exemplar of the power pole containing more info for said power pole, including a [Resource Key Type](/resource-key-type) pointing to the [S3D](/s3d) model, and monthly upkeep.
- Bitflag: Each possible power pole connection is defined by a 4 bit flag. The flag is presented in hex, but is evaluated in binary, with each of the 4 bits representing a direction, turned on or not. These define all 16 possible power pole connections from none allowed to all 4 directions allowed.

For example, look at the following line:

    0x0d=0x05000305

*0x0d* in [hex](/hexadecimal) is *1101* in binary, so all but connections in direction 2 are possible for this case.

### MiscNetworks

This section is depreciated and has no further function. Its original purpose was as a temporary solution to eliminate *z-fighting*, defined as when two objects try to render in the same space and one gets cancelled out. This property defined how many meters above terrain a particular network would be drawn, but has since been replaced by Maxis with a permanent solution to this problem.

### Bridge Exemplars

The Bridge Exemplars section is actually a series of subsections that contains a list of all bridge exemplars. The game refers to this list when dragging a network across water or a sufficiently deep/steep chasm. There is a subsection for each network type that has bridges.

Each subsection begins with a header identifying the type of network, followed by the actual list itself for that network type. The format of the list is:

    <bridgeID> = <TID>, <GID>, <IID>, <internal name>

For example,

    [RoadBridgeExemplars]
    1 = 0x6534284a, 0xa82ca30f, 0x00000001, level road bridge
    2 = 0x6534284a, 0xa82ca30f, 0x00000002, raised road bridge
    ...

The *bridgeID* is the bridge's internal ID and thus *must be unique within its own network*, however the same BridgeID can be used for each network. So, a Road bridge and a RHW bridge can both have an ID of 1, but two road bridges cannot both have BridgeID = 1. The BridgeID used here is identical to that used in the [Bridge RUL](/bridge-rul) files, for those bridges that have entries in that file. The combination of network type and BridgeID is how the game identifies any given bridge.

The listed TGI is that of the bridge parent-exemplar. This referenced bridge parent-exemplar file then follows on to reference child-exemplar files. These child-exemplar files are the EndPieceExemplars, RepeatPieceExemplars, and SupportPieceExemplars, and not only fall under the [Group ID](/group-id) specific format, but also a specific [Instance ID](/instance-id) format as well (which is believed to subsequently be controlled by the INI file itself, namely the section under Shadow Remappings). Note that not all of these three child-exemplar types will be present in every bridge parent-exemplar. They are each referenced by IID within the parent-exemplar.

The internal name is for reference only and not what is displayed in-game.

Essentially, the Network INI file and the referenced Bridge Parent-Exemplar files, control the "ability" to actually build a bridge. The [Bridge RUL](/bridge-rul) files are only supplementary after this; most of the bridges work without them.

### Tile Verifiers

Tile Verifiers are lines of [Individual Network RULs](/individual-network-ruls)-styled code that ensure that the Individual Network RULs (INRULs) and [RUL 0x10000002](/rul-0x10000002) (RUL2) changes are complete. If they aren't, the network drag fails (red draw).

The Maxis comments on this section from within the file are:

    ; Tile pattern verifiers are workarounds for the fact that
    ; we don't have full multitype rules -- basically, they
    ; enforce that a multistep patching solution completes.
    ; If all of the specified neighbor tiles aren't present,
    ; the center tile is booted as unsolved and the draw fails.
    ;
    ; Rule form:
    ;
    ;   base-pieceID = pos,pieceID,rot,flip [,pos,pieceID,rot,flip] [,pos,pieceID,rot,flip]...
    ;
    ; Positions are the same as for regular rules.  If multiple
    ; entries exist for a tile, the tile passes if any of the
    ; rules match.

Each (pos,pieceid,rot,flip) represents another tile to check for to validate the center tile.

The values for each entry are defined as:

- base-pieceID: The Instance ID of the exemplar for the base (center) tile to check outwards from.
- pos: Position of the check tile outwards from the center tile in a standard rotation starting at the top, if multiple matches exist, any of them may pass the check tile validation.
- rot: The rotation of the check tile to validate.
- flip: The flip, or lack thereof, of the check tile to validate.

An example entry is:

    0x04012200 = 3,0x04012300,3,1, 4,0x04003800,1,0, 5,0x04012300,0,0

This checks the tile with IID *0x04012200* to make sure the three required neighboring tiles are present in the required position in relation to itself, with the appropriate rotation and flip, or it can't be placed.

This is used in Maxis items such as avenue to elevated highway, ground highway to elevated highway, and in NAM items such as avenue turning lanes.

1.  [Network Specs](/network-specs)
