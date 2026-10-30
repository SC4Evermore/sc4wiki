---
title: "INFO"
description: ""
published: false
date: '2019-08-09T02:54:56Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-08-05T05:16:56Z'
---

The **INFO** format is basically a storage for all the data in the in-game picture albums. The description of the picture is kept in a text file, but all the rest of the data, including city name, mayor and other data is stored inside this format to save room. These files do not exist within [DBPF](/dbpf) files, but are freestanding .info files found in the Album folders.

There appear to be two types of info files. City pictures and region pictures, which have different structures. Each info file is comprised of sections identified by a 1 byte section header.

A note on the Picture/INFO type section seen below. This was deduced in the following way. No known settings in-game of any sort (night, underground, etc.) change this. It is the same for all cities in all regions. It is confirmed to be the same on other people's copies of the game. It doesn't change anything with the display. The picture/INFO type is all that's left. It might describe the next section in-game, but since [Maxis](/maxis) doesn't display the next section in-game anyways, that's unconfirmable, and it would still be picture/INFO type even if it did.

## City Pictures Format

     11 BYTES - "SanityCheck" in plain text (failed apparently ;-) )
     BYTE     - 71 (Start Username)
     X BYTES  - User name from your config-log in the SimCity 4 apps directory.
     BYTE     - 71 (Start City name)
     X BYTES  - City name one byte per letter including spaces
     BYTE     - 71 (Start Mayor Name)
     X BYTES  - Mayor Name, one byte per letter
     BYTE     - 71 (Start of Julian Date)
     7 BYTES  - Julian date of picture, game date, not real world.
     BYTE     - 71 (Start Date of Picture)
     X BYTES  - Date of picture, game date, not real world.
                In MM/DD/YY with leading zeros in the month and day left out.
                For example, 11/10/86 or 3/1/57.
                May vary based on local conventions - hence use of JD in previous field.
     BYTE     - 71 (Start Population)
     X BYTES  - Population
     BYTE     - 71 (Start Funds)
     X BYTES  - City Funds
     BYTE     - 71 (Start Picture/Info Type)
     2 BYTES  - Picture/INFO type (values of 27 or 45)
     BYTE     - 71 (Start picture info)
     X BYTES  - Picture info, comma delimited
                Zoom (1 byte), Rotation (1 byte), X position (3 bytes), Z position (3 bytes).
     BYTE     - 71 (End File)

- Zoom is a number, from out to in, 0-5.
- Rotation is a number for the direction the picture is facing. 0=North, 1=East, 2=South, 3=West.
- X and Z positions are measured in tiles, from 0,0.

## Region Pictures Format

The data stored in these files is the same as the picture filename. For example "Region name-Timestamp.PNG".

     X BYTES  - Region name
     BYTE     - 56 (-)
     10 BYTES - Timestamp for time picture was taken
     BYTE     - 55 (.)
     3 BYTES  - PNG

## Character Table

Note that while these files can be opened with a hex editor, they must be translated using the character table below to be readable.

    --Numbers 0-9:
    4b,4a,49,48,4f,4e,4d,4c,43,42

    --Characters A-Z (capitals):
    3a,39,38,3f,3e,3d,3c,33,32,31,30,37,36,35,34,2b,2a,29,28,2f,2e,2d,2c,23,22,21

    --Characters a-z (lowercase):
    1a,19,18,1f,1e,1d,1c,13,12,11,10,17,16,15,14,0b,0a,09,08,0f,0e,0d,0c,03,02,01

    --Special Characters (table):
    (space),-  ,~  ,.  ,{  ,}  ,|  ,`  ,[  ,_  ,^  ,]  ,\  ,@  ,;  ,:  ,?  ,>  ,=  ,<  
    5b     ,56 ,05 ,55 ,04 ,06 ,07 ,1b ,20 ,24 ,25 ,26 ,27 ,3b ,40 ,41 ,44 ,45 ,46 ,47

    +  ,'  ,)  ,(  ,/   ,, ,#  ,"  ,!  ,*  ,&  ,%  ,$ 
    50 ,51 ,52 ,53 ,54 ,57 ,58 ,59 ,5a ,5c ,5d ,5e ,5f
