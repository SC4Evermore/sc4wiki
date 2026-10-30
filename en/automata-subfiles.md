---
title: "Automata Subfiles"
description: ""
published: true
date: '2023-02-19T09:14:24Z'
tags: ["Savegame/Subfiles"]
editor: markdown
dateCreated: '2023-02-11T19:39:23Z'
---

This page pertains to the format of the **Automata Subfiles** within the [Savegame](/savegame) files.

# Vehicle Automata Subfile (0x896e714a)

## Structure

List of records of the form:

    DWORD           Record Size
    DWORD           CRC
    DWORD           Memory address
    WORD×4          Version (always 2, 2, 8, 4)
    DWORD           Appearance flags (See Appendix 1.4)
    DWORD           Record type identifier (always 0xc7cc75f1)
    ARBIT           Record substructure (See Appendix 1.1)

## Appendix 1.1 - Record substructure 0xc7cc75f1

    BYTE×4          (Min Tract X, Min Tract Z, Max Tract X, Max Tract Z) coordinate
    WORD×2          Tract size (X, Z)
    DWORD           Count of properties
        SGPROP      SaveGame Properties, repeated Count times (e.g. Occupant Group property 0xAA1DD396)
    DWORD×3         (Group=0x096E6739, Type=0x6534284A, Instance)-ID of Exemplar
    FLOAT32×3       (x, y, z)-coordinate A
    FLOAT32×3       (x, y, z)-coordinate B or (-1, -2, -3)
    FLOAT32×3       Direction (a unit vector)
    FLOAT32         Unknown scalar (approximately satisfies: coordinate A + direction * scalar / 2 = coordinate C)
    FLOAT32         Speed in km/s (in range 80..110 km/h defined in Automata Controller)
    DWORD           Unknown bitset
    DWORD           Unknown (always 0)
    DWORD           Address
        DWORD       Subfile (Automata Attractor subfile) when Address is not 0
    FLOAT32×5       Unknown (the last three are 0.0 if the attractor is absent, so might be related parameters)
    DWORD           Address
        DWORD       Subfile (e.g. Trailer Vehicle, Ambulance, Bus, Patrol Car) when Address is not 0
    DWORD           Count of blocks to follow
        DWORD       Unknown (seen 0, 7, 13)
        WORD        Unknown (always 0x03)
        DWORD       Address
            DWORD   Subfile (Automata Generator or Attractor subfile) when Address is not 0
        DWORD       Index of block starting at 0, 1,...
        FLOAT32     Unknown (-1.0 or large numerical values)
        DWORD       Unknown (0 or 1)
        BYTES×5     Unknown (always 0)
        DWORD       Unknown bitset
    DWORD           Count of auxiliary models
        DWORD×3     TGI of auxiliary S3D-model (e.g. head lights, rear lights)
    DWORD×3         TGI of S3D-model
    DWORD           Instance ID
    DWORD           Count of manager addresses
        DWORD       Address
        DWORD       Subfile (e.g. City Situation Manager or Automata Controller Manager)
    FLOAT32         Speed in km/s (can differ from other speeds)
    FLOAT32         Speed in km/s (can differ from other speeds)
    FLOAT32×6       Unknown (often 0 or 1, but numerical values are possible)
    BYTE            Unknown (seen 0, 25, 50, 254)
    DWORD           Occupant Group
    DWORD           Address
        DWORD       Subfile (e.g. Trailer Vehicle, Ambulance, Bus, Patrol Car) when Address is not 0
    DWORD           Travel type (See Appendix 1.2)
    BYTE            Unknown (in range 0...47 -- maybe vehicle lifespan?)
    DWORD           Address of network tile
        DWORD       Subfile (e.g. Network Subfile 1, Prebuilt Network Subfile, Bridge Subfile) when Address is not 0
    BYTE            Exit side of path (0,1,2,3 = W,N,E,S)
    BYTE            Entry side of path (0,1,2,3 = W,N,E,S)
    BYTE            Path class number
    BYTE            Path transport type (See Appendix 1.3)
    DWORD           Index number of the Path Coordinate Point the vehicle is headed to next
    DWORD           Count of tiles (presumably tiles to stop at -- seen nonzero for Occupant Group Moving Van)
        BYTE        Tile number X
        BYTE        Tile number Y
        BYTE        Unknown (seen only 0x01)
    DWORD           Count of tiles (consecutive from furthest to closest -- seen nonzero for trains)
        BYTE        Exit side of path (0,1,2,3 = W,N,E,S)
        BYTE        Entry side of path (0,1,2,3 = W,N,E,S)
        BYTE        Path class number
        BYTE        Path Transport Type (See Appendix 1.3)
        DWORD       Tile number X
        DWORD       Tile number Y
    DWORD           Unknown (always 0)
    FLOAT32×3       (x, y, z)-coordinate C or (-1, -2, -3)
    FLOAT32×3       (-1, -2, -3)
    FLOAT32         Unknown (often 0.0)

For the format of the properties, see [SaveGame Properties](/network-subfiles#appendix-2-1-structure-of-sgprop-savegame-properties).

## Appendix 1.2 - Travel Types

    0 - None
    1 - Commute
    2 - Bus
    3 - Freight Truck
    4 - Commute Train
    5 - Freight Train
    6 - Subway
    7 - Occupant Trip
    8 - Crime
    9 - El Train
    10 - Monorail

## Appendix 1.3 - Path Transport Types

See [Transport Type Values](/sc4path-format#transport-type-values).

## Appendix 1.4 - Appearance Flags

    0x01000000 - Unknown
    0x04000000 - Unknown
    0x10000000 - Unknown

(Seen 0x10000000, 0x11000000, 0x14000000, 0x15000000 for automata in game.)

# Mass Transit Train Subfile (0x4c22ae53)

This file contains automata for Elevated Rail and Monorail.

## Structure

List of records of the form:

    DWORD           Record Size
    DWORD           CRC
    DWORD           Memory address
    WORD×7          Version (always 1, 2, 2, 2, 2, 8, 4)
    DWORD           Appearance flags (See Appendix 1.4)
    DWORD           Record type identifier (always 0xc7cc75f1)
    ARBIT           Record substructure (See Appendix 1.1)
    DWORD           Count of train cars
        DWORD       Address
        DWORD       Subfile (e.g. Train Car subfile)
    DWORD           Unknown (seen 3...8)
    FLOAT32         (x, y, z)-coordinate (can be far away from other coordinates)
    DWORD           Address of 2nd network tile
        DWORD       Subfile (e.g. Prebuilt Network subfile) when Address is not 0
    BYTE            Exit side of path (0,1,2,3 = W,N,E,S)
    BYTE            Entry side of path (0,1,2,3 = W,N,E,S)
    BYTE            Path class number
    BYTE            Path transport type (See Appendix 1.3)
