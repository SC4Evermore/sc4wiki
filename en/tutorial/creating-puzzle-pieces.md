---
title: "Creating Puzzle Pieces"
description: ""
published: false
date: '2019-08-04T05:46:35Z'
tags: ["Transit Networks", "Transit Modding"]
editor: markdown
dateCreated: '2008-09-20T11:17:54Z'
---

## Creating puzzle pieces

### What do you need?

- Basic understanding of the [reader](/reader).
- Notepad (or equivalent, but I advise against Word).
- Models and Path files for the [puzzle piece](/puzzle-piece).

### Exporting the RUL file

Skip this section if you are used to the reader and know how to export files from it.  
Because the file RUL files are so large they can’t be modified in the reader, so we have to export them and open them in notepad.  
To do this we first open the NetworkAddonMod_Controller.dat file ([NAM Controller](/nam-controller)) in the [reader](/reader).  
You should see 4 files, 1 [DIR](/dir) and 3 [RUL](/rul) like below  
<http://i200.photobucket.com/albums/aa230/warriorST/Private/IMG1.jpg>  
Right click on the RUL file with the [Instance ID](/instance-id) (IID) of 10000000 (this is the puzzle piece RUL). This will bring up a fairly long context menu.  
  
<http://i200.photobucket.com/albums/aa230/warriorST/Private/IMG2.jpg>  
  
Click “Save decoded file”, the second option from the top. And this box will appear. Which tells you the name of the file and that it has been saved.  
  
<http://i200.photobucket.com/albums/aa230/warriorST/Private/IMG3.jpg>  
  
Now in Windows, browse to your Network Addon Mod folder and you should see the file you just saved along with another one with the same name except it has “.TGI” on the end.

1.  Rename the file circled in red to “Puzzle Piece.rul”
2.  Rename the file circled in green to “Puzzle Piece.rul.TGI”
3.  The two file names must always match except for the “.TGI” on the TGI file.  

  
<http://i200.photobucket.com/albums/aa230/warriorST/Private/IMG4.jpg>  
  

### Creating the puzzle piece

The first thing you need to do is get a HID (hex-ID), this is 4 digits long and identifies the puzzle piece.

For testing we use the range F###.

So open the Puzzle Pieces.rul file you just saved. Now click at the very top of the document. Press Ctrl-F to open find and type in F000, there should be no results, this means it is available to use.

Now scroll down to the very bottom, and paste this template in.

    [HighwayIntersectionInfo_0x0000'''XXX'''0]
    ;Added by '''USERNAME DATE'''.
    ;'''DESCRIPTION'''
    Piece = 0.0, 0, 0, 0, '''PREVIEWIID'''
    PreviewEffect = '''PREVIEWNAME'''

    CellLayout =.......
    CellLayout =......<
    CellLayout =..^....

    '''CHECKTYPES'''

    ConsLayout =.......
    ConsLayout =......<
    ConsLayout =..^....

    AutoTileBase = '''ATBIID'''
    PlaceQueryID = '''PQIID'''
    Costs = 50

    [HighwayIntersectionInfo_0x0000'''XXX'''1]
    CopyFrom = 0x'''XXX'''0
    Rotate  = 1
    [HighwayIntersectionInfo_0x0000'''XXX'''2]
    CopyFrom = 0x'''XXX'''0
    Rotate  = 2
    [HighwayIntersectionInfo_0x0000'''XXX'''3]
    CopyFrom = 0x'''XXX'''0
    Rotate  = 3
    ;Rotation Clones
    [HighwayIntersectionInfo_0x0000'''XXX'''4]
    CopyFrom = 0x'''XXX'''0
    [HighwayIntersectionInfo_0x0000'''XXX'''5]
    CopyFrom = 0x'''XXX'''1
    [HighwayIntersectionInfo_0x0000'''XXX'''6]
    CopyFrom = 0x'''XXX'''2
    [HighwayIntersectionInfo_0x0000'''XXX'''7]
    CopyFrom = 0x'''XXX'''3

First off, we need to replace all the words in Capital and with ''' surrounding them.

1\) Replace **XXX** with the first 3 digits of your HID, in this case F00. This is what links the actual RULs to the Ordering Section at the top.

2\) Replace **USERNAME** with your Username. This is just for reference.

3\) Replace **DATE** with the current date. This is just for reference. (To limit confusion, use the date format DD-MON-YEAR, eg 02-Oct-2008)

4\)

preview_constructionmedium
