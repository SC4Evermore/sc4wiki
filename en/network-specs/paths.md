---
title: "Network Specs/Paths"
description: ""
published: false
date: '2019-08-04T05:45:29Z'
tags: ["Network Specs"]
editor: markdown
dateCreated: '2008-11-11T20:20:49Z'
---

When the original version of [SimCity 4](/simcity-4) was released, there were two [Path](/sc4path) file versions, 1.0 & 1.1. [Rush Hour](/rush-hour) saw the introduction of a third version, 1.2. The "Header" below is the starting point of a Path. The whole specs are further below. This path file has just been provided as a sample.

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

## Specific Format

### Header

    SC4PATHS - Header
    1.2      – Path file version. There is: 1.0  1.1  1.2.
    3        - Number of Normal Path Sections in file. Includes Normal Paths for any valid Transport Type.
               Does not include Stop Sections.
    0        - Number of Stop Path Sections in file. Includes Stop Paths for any valid Transport Type.
               Does not include Normal Paths.
    1        - Terrain variance (This is the End of the Header section)

### Normal Section/Path

This can usually include comments about the following Path.

1 - Transport Type. Or in other words, the different modes of transport. See table below.  
1 - Class/Path number. 0 to infinite. The actual limit is not known. There can exist a lot of Paths for the same Transport type with same Entry/Exit points.  
2 - Entry side/point  
3 - Exit side/point  
0 – Junction Key (only found in 1.2 version. Rail-based networks make use of the JunctionKey for U-Drive-It)  
4 – Number of Path, or rather Plotting Points or Coordinate lines that follow.

<font color="blue"> First Coordinate "Line" is the</font><font color="red"> Entry Point position.</font>

<font color="blue"> Last Coordinate "Line" is the</font><font color="red"> Exit Point position.</font>

<font color="blue"> X1 - Coordinate line1  
X2 - etc  
X3  
X4  
</font>End of normal path/Section, and/or File. Repeat for each "normal" path/section within a Path file.

### STOP Paths

It is very important that any & all STOP Paths are done \*AFTER\* ALL normal Paths, otherwise the game can & will crash.

1 – Left/Right hand side. Or UK/US  
7 – Transport Type. See table below  
1 - Class/Path number. 0 to infinite. The actual limit is not known. There can exist a lot of Paths for the same Transport type with same Entry/Exit points.

<font color="red"> 2 - Entry side  
3 - Exit Side  
</font>

<font color="blue"> X1 - Coordinate line1  
</font> For stop paths, this is just one line as they are stopping points.

End of Section (and/or file). Repeat for each section within a Path file.

## Versions

The different versions have slightly different formats to them, but the specs above should help understand them. Typically, if creating new paths and/or path files, try to use version 1.2 as it contains all formats of previous versions. Be mindful of changing the version of an existing file though, as all Paths within the file may need changing if the version is changed.

## Transport Type

1.  Car.
2.  Sim.
3.  Train (surface rail).
4.  Subway.
5.  Supposedly not used.
6.  Elevated Train.
7.  Monorail.

## Class/Path Number

If the Transport Type is the same and the Entry & Exit Points are the same for two or more Paths, then this Class/Path Number must contain a non-zero number. So if there are 4 Car Paths which go from side 2 to side 3, each path must have a unique class/path designation. A zero in this value defines it as the only path of its type with the stipulated entry/exit sides. So if you add a path to a 1.1 or 1.2 version file which has a zero as the path number for the tile entry/exit combination you want to use, you must change the existing path's class/path number to something other than zero, otherwise the whole Path file may be void.

## Junction Key

This is only found in version 1.2.

Basically *0* denotes no junction and *1* defines the path as a junction (one entry point to more than one exit point). This is used for [U-Drive-It](/u-drive-it) vehicles, such as Trains.

## Entry/Exit values

`0=West, 1=North, 2=East, 3=South`  
`255=special type. i.e. neighbour connections, end stubs and others.`

## Coordinate Values

    Positive x=East,
    Negative x=West,
    Positive y=North,
    Negative y=South.

    Or alternatively;
    North = positive 'X' values.
    South = negative 'Y' values.
    East = positive 'X' values.
    West = negative 'X' values.
    Z = Height. 0 = Ground.
    Min/Max [for NSEW] = -8 to 8.
           - Values outside of this may cause automata to do funny things, 
             and even cause the Path file not to function properly.

NOTE: for the Coordinate Lines, it's a good idea to take a look at the Piece/File/Rules that the Path(s) are for, especially when the height of the network piece moves.

## General notes

When SimCity 4 was originally released, Cars would jump from a highway to an underneath road without any existence of ramps (under certain circumstances). This is something that Maxis fixed. Unfortunately, networks still have some limitations and/or issues with them related to Paths, which subsequently affects normal path routing and also U-Drive-It. These limitations/issues are more noticeable with some of the custom-made items that have been made for the game. So just be aware of this.

The [Group ID](/group-id) (GID) for the Path file(s) is dependent on whether or not the tile in-game is a 3D model or just plain texturing.

- Path file GID for 3D Model tile(s): *0xA966883F*
- Path file GID for Texture tile(s): *0x69668828*

The following is a simple diagram of how Entry/Exit Points & Path Coordinates works for any single Path for any given Transport Type. ![](/_files/images/nspath1.jpg)
