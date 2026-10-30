---
title: "SC4Path Format"
description: ""
published: false
date: '2019-08-04T05:43:38Z'
tags: ["Transit Modding", "MTS2"]
editor: markdown
dateCreated: '2012-10-13T02:44:31Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**[SC4Path](/sc4path)** files define where the game's [automata](/automata) travel on transit networks. Each tile of network in the game has a corresponding SC4Path file that defines the available paths across that tile. SC4Path files share [Instance IDs](/instance-id) with the corresponding [exemplar](/exemplar) and [S3D](/s3d) file (if any) for that particular network piece.

The [Group ID](/group-id) (GID) for path files is dependent on whether or not the network tile in-game is a 3D model or just a texture.

- SC4Path file GID for 3D Model tile(s): *0xA966883F*
- SC4Path file GID for Texture tile(s): *0x69668828*

Generally, SC4Path files begin with a header, containing version and file information, followed by repeating chunks of data that contain the actual path information.

An example SC4Path file is included at the end of this page for reference.

## Versions

SC4Path files come in three different versions, namely 1.0, 1.1, and 1.2. The first two were included in the original release of [SimCity 4](/simcity-4), and the third was introduced in [Rush Hour](/rush-hour). All three versions can be used simultaneously in the game. The format of each version may vary slightly.

Typically, when creating new paths and/or path files, it is recommended to use version 1.2 as it contains all formats of previous versions. Be mindful of changing the version of an existing file though, as all Paths within the file may need changing if the version is changed.

The different versions have slightly different formats to them, but the specification below should enable you to work within the format of all three versions.

- **Version 1.0** may not contain stopped automata detail (Stop Paths).
- **Version 1.1** has everything in Version 1.0, plus Stop Paths, and the additional header item listing the number of Stop Paths.
- **Version 1.2** has everything in Version 1.1, plus Junction Keys.

## Header

The header specifies the path "version", the number of Normal Paths contained within, and the number of Stop Paths contained within.

    SC4PATHS - Filetype (always the same).
    #.#      – Path file version. Options are: 1.0, 1.1, 1.2.
    #        - Number of Normal Path Sections in file. Includes Normal Paths for any valid Transport Type.
               Does not include Stop Sections.
    #        - Number of Stop Path Sections in file. Includes Stop Paths for any valid Transport Type.
               Does not include Normal Paths. Exists in Versions 1.1 and 1.2 only.
    BOOL     - Terrain variance, or 3D Key.
               0 = Path follows parallel to terrain.
               1 = Path does not hold to terrain.

## Normal Paths Block

The header is followed by repeating **Normal Paths**, if any. This section can usually include comments about the following Path. They have the following format.

    -- Type_Class_EntrySide_ExitSide
         - Transport section internal name.
           Note: Class is not present if not set.
    #    - Transport Type - Which mode of transit this path applies to. See table below for values.
    #    - Path number. 0 to infinite. The actual limit is not known.
           There can exist a lot of paths for the same transport type with same Entry/Exit points.
    #    - Entry side. See below for values.
    #    - Exit side. See below for values.
    BOOL – Junction Key - Rail-based networks make use of the Junction Key for U-Drive-It. Exists in v1.2 only.
    #    – Number of path plotting points that follow.
    [Path Points]

The path points are presented as a list of coordinates in Z,X,Y format. The first point is the Entry Point position, and the last point is the Exit Point position. Intermediate coordinates define the path between the Entry and Exit Points.

This block repeats for each Normal Path within a SC4Path file.

## Stop Paths Blocks

**Stop Paths** must be after all Normal Paths, if they are present in the file, otherwise the game can and will crash. Note that these are not present in Version 1.0 files.

    -- Stop_TransitType_Class_EntrySide_ExitSide
      - Stop section internal name.
        Will begin with StopUK for UK stop paths.
        Note: Class is not present if not set.
    # – Type of Stop (Left/Right hand drive).
        1 = Right side (US).
        2 = Left side (UK).
    # – Transport Type - Which mode of transit this path applies to. See table below for values.
    # - Path number. 0 to infinite. The actual limit is not known.
        There can exist a lot of paths for the same transport type with same Entry/Exit points.
    # - Entry Side. See below for values.
    # - Exit Side. See below for values.
    [Stop Point]

The Stop Point is presented as a coordinate in Z,X,Y format. For stop paths, this is just one line as they are stopping points.

This block repeats for each Stop Path within a SC4Path file.

## Class

The different values for this are for various types of movement, i.e. high to low highway, what side and direction for on-ramps, what junction movement for trains. In the end these are just the path number of the tile. However, assigning proper classes to them makes things much easier to read. These do not appear to be case sensitive values.

The examples below show the use in the Internal Name at the start of the Path Blocks, with the TransitType_Class format:

    xxx_a,b,c      - Standard path numbers for lanes on network types. "xxx" is network type.
    car_i,o        - Highway cloverleaf ramps to switch between highways.
    car_d,e,f      - On and off ramps
    sim_*          - These are found in intersections. Possibly a large range of values.
    train_d,e      - These are found when trains have a junction where all four tracks enter and exit from the same side of the tile.
    Car(stopped)_* - Various car stopping positions for an intersection.

## Transport Type Values

    1 Car
    2 Sim (Pedestrian)
    3 Train (surface rail)
    4 Subway
    5 Supposedly not used
    6 Elevated Train
    7 Monorail

## Path Number

If the Transport Type is the same and the Entry and Exit Points are the same for two or more Paths, then this Path Number must contain a non-zero number. So if there are four car paths which go from side 2 to side 3, each path must have a unique class/path designation. A zero in this value defines it as the only path of its type with the stipulated entry/exit sides. So if you add a path to a 1.1 or 1.2 version file which has a zero as the path number for the tile entry/exit combination you want to use, you must change the existing path's class/path number to something other than zero, otherwise the whole path file may be void.

## Junction Key

The Junction Key is only found in version 1.2. Basically *0* denotes no junction and *1* defines the path as a junction (one entry point to more than one exit point). This is used for [U-Drive-It](/u-drive-it) vehicles, such as trains.

## Entry/Exit Side Values

`0  = West`  
`1  = North`  
`2  = East`  
`3  = South`  
`255= Special type. i.e. neighbour connections, end stubs and others.`

## Coordinate Values

Values used in Path or Stop Point coordinates use the following format:

    Positive X = East,
    Negative X = West,
    Positive Y = North,
    Negative Y = South.

Or alternatively:

    North = positive 'X' values.
    South = negative 'Y' values.
    East  = positive 'X' values.
    West  = negative 'X' values.

The Min/Max for NSEW values is -8 to 8. Values outside of this may cause automata to do funny things, and even cause the path file not to function properly.

    Z = Height. 0 = Ground.

The following is a simple diagram of how Entry/Exit Sides and Path Coordinates works for any single Path for any given Transport Type. Entry/Exit Sides are in red, Path Coordinates are in blue. ![ \|none\| \| ](/_files/images/nspath1.jpg)

*Note:* for the Path and Stop Point coordinates, it is a good idea to take a look at the Piece/File/Rules that the path(s) are for, especially when the height of the network piece moves.

## General Notes

When [SimCity 4](/simcity-4) was originally released, cars could jump from a highway to a road below without the existence of any ramps under certain circumstances. This is something that Maxis fixed. Unfortunately, networks still have some limitations and/or issues with them related to paths, which subsequently affects normal path routing and also [U-Drive-It](/u-drive-it). These limitations/issues are more noticeable with some of the custom-made items that have been made for the game.

## Example SC4Path File

<font color="green" face="Courier New"> SC4PATHS  
1.1  
2  
3  
0  
-- Car_3_1  
1  
0  
3  
1  
2  
2.5,-8.0,0.0  
2.5,8.0,0.0  
-- Sim_3_1  
2  
0  
3  
1  
2  
2.5,-8.0,0.0  
2.5,8.0,0.0  
-- stopUK_car_1_255  
2  
1  
0  
1  
255  
2.54713,7.26555,0.0  
-- stop_car_1_255  
1  
1  
0  
1  
255  
-2.51329,7.24569,0.0  
-- stop_sim_a_0_255  
1  
2  
1  
0  
255  
-5.00628,6.41454,0.0  
</font>

1.  [Network Specs/Paths](/network-specs/paths)
