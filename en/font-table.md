---
title: "Font Table"
description: ""
published: false
date: '2019-08-04T05:41:01Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-22T18:01:36Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

The **Font INI** contains information regarding the in-game fonts, and is located at [TGI](/tgi) *0x00000000,0x4a87bfe8,0x2a87bffc*. The description of the Font INI file is quite simple and is provided by Maxis within the file itself for the most part. Most of the following specification comes from that description.

## Specification

This file is composed of multiple lines, each of which describes font specification. The format of each line is this:

     <style name> = <font face name list>, <size>, <style parameters separated by |>, <GUID>

The variables used above are defined as follows:

    style name          = The in-game used name for the font.
    font face name list = The list of fonts to use for this style name separated by commas.
                          Values after each comma are used if the font before it is unavailable.
    size                = The font size for use in-game.
    style parameters    = How to render the font according to a list or properties separated by a |.
                          See below for the full list of available properties.
    GUID                = The arbitrary GUID to assign to this font for use in the game.

### Examples

A simple example of this is:

`NewsBody = "Arta", "14", "Italic", 0xeadd276d`

The above states that we have a font style called "NewsBody" which uses the face name Arta, is size 14, italic, and has been assigned the arbitrary GUID of 0xeadd276d.

A more complicated example is this:

`NewsBody = "Arta, Arial", "14", "Bold | Italic | LineSpacing=2 | aa=bg | underline", 0xeadd276d`

The above states that we have a font style called "NewsBody" which uses the face Arta but falls back to Arial if Arta isn't available, is size 14, and is bold, italic, has a line spacing of 2, is antialiased to the background and is underlined and has been assigned the arbitrary GUID of 0xeadd276d.

### Style Parameters

Here is the full current list of supported style parameters with explanations and examples where useful:

    Bold                    Requests a boldened version of the font.

    Italic                  Requests an italicized version of the font.

    Underline               Requests an underlined version of the font.

    Strikethrough           Requests a strikethrough (line through middle) version of the font.

    Shadow                  Requests a shadowed version of the font.

    XScale=1.0              Requests a font with a given horizontal scaling.
                            Values are in the floating point range of 0.1 to 10.0. 1.0 is default;
                            0.5 shrinks the font horizontally by half. Example: XScale=1.25

    YScale=1.0              Requests a font with a given vertical scaling.
                            Values are in the floating point range of 0.1 to 10.0. 1.0 is default;
                            0.5 squashes the font vertically by half. Example: YScale=0.85

    AA=None | BG | Color    Request one of three anti-aliasing modes: none, antialias to the background,
                            or anti-alias to a specific color (specified by the BGColor parameter). Example: AA=BG

    Color=r,g,b             Requests a font with the given foreground RGB color.
                            Values are in the range of integers of 0-255, inclusive. Example: Color=234,12,0

    BGColor=r,g,b           Requests a font with the given background RGB color.
                            Values are in the range of integers of 0-255, inclusive. Example: BGColor=234,12,0

    Gamma=1.0               Requests a font with the given 'gamma' value.
                            Values are in the range of floating point 0.0-10.0. A gamma of 1.0 is default,
                            with higher values resulting in lighter font edges and lower values
                            resulting in darker font edges. Example: Gamma=1.25

    Sharpness=0.0           Requests a font with a given anti-aliasing sharpness. A sharpness of 0 is default,
                            with negative values being somewhat blurry and positive values
                            being somewhat sharp. Example: Sharpness=0.1

    CharSpacing=0           Requests a font with a given horizontal character pixel spacing adjustment.
                            Adds or subtracts pixels between characters. Values are in the range of integers
                            between -10 and +10. Example: CharSpacing=-1

    LineSpacing=0           Requests a font with a given vertical line spacing pixel adjustment.
                            Adds or subtracts pixels between lines by adding pixels to the top of each line.
                            Values are in the range of integers between -10 and +10. Example: LineSpacing=3 

    XAdvanceScale=1.0       Requests a font with a given horizontal 'advance' scaling.
                            Advance refers to the distance from the start of one character to the start
                            of the next. Note that XAdvanceScale is different from XScale
                            because XAdvanceScale doesn't scale the character but only the distance
                            between characters. Values are in the range of 0.1 - 10.0. Example: XAdvanceScale=0.95
