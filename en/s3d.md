---
title: "S3D"
description: ""
published: false
date: '2019-08-09T02:55:01Z'
tags: ["File Formats/SC4"]
editor: markdown
dateCreated: '2009-02-06T22:17:04Z'
---

**SimGlide 3D Models (S3D)**, are the models contained in [DBPFs](/dbpf). These models are used for almost all 3D objects in the game, including buildings, props, some transport networks, and bridges. An explanation on their format can be found at [S3D Format](/s3d-format). Most standard buildings and props are actually boxes with a texture applied to give the effect of being 3D. However, network models are almost always [True3D](/true3d), meaning that they are actually fully 3D models.

S3D files may have the following [Group IDs](/group-id):

- 0xbadb57f1 - Buildings/3D Networks/Advisors/Fauna/Automata
- Other - Buildings exported from [BAT](/bat).

Parents of S3D files may include:

- Lot [Exemplars](/exemplar)
- Transit [Exemplars](/exemplar) (such as Highway Exemplars)
- [Effect Directories](/effdir)

Children of S3D files may include:

- [FSH](/fsh)

See the [Relations](/relations) page for more information about how S3D files interact with other files.

## S3D Modding information by smoncrie

The following section was primarily [written by smoncrie](http://sc4devotion.com/forums/index.php?topic=1145.msg390190#msg390190). Some corrections and additions have been made.

### S3D Overview

When you look at an S3D in Reader you can see a number of tabs. The important ones are: Vert, Indx, Prim, Mats, and Anim.

Vert  
Contains lists of points, collected into groups.

<!-- -->

Indx  
This contains lists of triangles, collected into groups. Each line in Indx contains 3 numbers. Each number specifies a point in Vert. The three points are the corners of the triangle.

Note that the same point can be used in several triangles.

<!-- -->

Prim  
Contains a list of numbers; each number is 3 times the number of triangles that will be used. Usually this is exactly 3 times the number of triangles listed in one of the groups in Indx.

<!-- -->

Mats  
Contains a list of textures.

<!-- -->

Anim  
Contains a list of objects. Each Anim entry contains at least one line of 4 numbers.

  
The first number points to a group in Vert.

The second number points to a group in Indx.

The third number points to number in Prim.

The fourth number points to a texture in Mats.

<!-- -->

  
Thus we start with a group of points in Vert, and arrange them into triangles according to the specified group in Indx, but we only use the number of triangles specified in the Prim entry. All these triangles will be painted with the given Mats texture. Collectively all this forms the object.

<!-- -->

  
Note that the values in Anim entries do not have to be unique, so for example the same Indx group may be used in several Anim entries, but with different Vert groups or different textures.

<!-- -->

  
Of course there are limits. You are likely to crash SimCity if not all the points specified in the Indx group exist in the Vert group, or not all the triangles specified in the Prim entry exist in the Indx group.

### S3D Details

#### Vert

X, Y, Z are the coordinates of the point in meters. For transport models, (0,0,0) is the centre of a 16m X 16m SimCity tile.

  
X: Left \<= Smaller value; Larger value =\> Right

Y: Low \<= Smaller value; Larger value =\> High

Z: Far \<= Smaller value; Larger value =\> Near

Note the Z coordinate is the reverse of what one might expect.

U and V specify a point in the texture:

U: is left/right where 0 is the left side, 0.5 is the centre, and 1 is the right side. V: is bottom/top where 0 is the bottom, 0.5 is the centre, and 1 is the top. Note: If U or V is less than 0 or greater than 1 see Wrap mode U and Wrap mode V in Mats.

For simple models that reference flat textures only, there are usually four lines in a group with all U and V values all being exactly 0 or 1. In such a case, you can easily rotate and mirror textures by exchanging 0 and 1 values in a systematic way. For example, exchanging all values in a U column will mirror in U-direction. A rotation can be achieved, e.g., by changing "U V" values from "0 0" to "1 1" and from "1 1" to "0 0". If the texture is included in the same dat-file, the preview shows the immediate effect and it usually takes only few trials to achieve the desired rotation or mirror. For rotating or mirroring more complex models, see the section below on "Working with a Spreadsheet".

#### Indx

The values in Indx specify the three corners of a triangle with an (X,Y,Z) position for each corner. The order of the corner points is important. If the corners surround the centre of the triangle in counter-clockwise order, the triangle will be VISIBLE; if the corners surround the centre in clockwise order, and the backface culling field is checked (this field is in Mats), the triangle will be INVISIBLE.

Reader does not handle the visibility of triangles properly. Several times I have had a model that looked fine in reader, but had missing (invisible) triangles when used in the game. To make a triangle visible, find the triangle in Indx and swap any two of the numbers.

The corners also each have U,V values that specify how the texture is to be mapped onto the triangle. Imagine the triangle is made of wood and positioned in the air like a piece of modern sculpture, and that you have a piece of stretchy fabric painted on both sides with the given texture. Find the point on the fabric specified by the U,V values and nail that point of the fabric to the corner of the triangle. For the other two corners of the triangle, stretch the corresponding U,V points of the fabric over to the triangle corners and nail them in. The fabric will now be stretched over the triangle in the same way that SimCity maps the texture onto the triangle.

#### Mats

I confess that I do not know what all the values mean here…

Material Name  
A description of the texture.

<!-- -->

Material ID  
The Instance ID of the texture. For transport models, texture Group ID is often 0x1abe787d; otherwise the Group ID of the S3D will also be used as the Group ID of the texture.

<!-- -->

  
If the current S3D is one of a group of 20 S3D’s specified by Resource Key Type 1 (an exemplar property), night lighting textures (if any) will have an Instance ID that is the specified Instance ID plus 0x800.

To see the rest of the Mats values you will usually need to click on the texture’s Material ID field and drag down on the vertical scroll bar. If there are two vertical scroll bars, use the right scroll bar.

alpha test  
If checked, use the texture’s alpha map.

<!-- -->

  
White alpha map values mean that part of the texture is visible. Black values mean that part of the texture is invisible. Gray values mean that part of the texture is partially visible (transparent). This only works if other Mats fields are set. In any case SimCity ignores anything but large changes in gray value.

<!-- -->

depth test  
If this is NOT checked, the object will always be visible, even if it is behind another object. For S3D models that are used as preview, it should be not checked.

<!-- -->

backface culling  
Make a triangle invisible if its corners are in clockwise order around the triangle’s centre. See Indx.

<!-- -->

framebuffer blending  
Usually this is ONLY checked for transparent textures or for some transportation textures (E.g. road) at ground level.

<!-- -->

texturing  
Usually checked. If it is not checked the object will not be visible.

<!-- -->

Alpha Func  
This should be set to greater.

<!-- -->

Depth Func  
This should usually be set to less than or equal. I have also used less than.

<!-- -->

Src Blend  
Usually one. Other values like source alpha can be used for transparent textures.

<!-- -->

Dest Blend  
Usually zero. Other values like one minus source alpha can be used for transparent textures.

<!-- -->

Wrap mode U  
This specifies what is done with U values (from Vert) that are less than 0 or greater than 1.

<!-- -->

  
**repeat** specifies that the texture is to be repeated to the left and right. For example:

  
1.3 points to one repeat to the right

2.4 points to the second repeat to the right

-0.5 points to one repeat to the left

-1.6 points to the second repeat to the left

Etc.

**clamb** (a misspelling of "clamp") specifies that the repeat textures are mirror imaged. This is sometimes useful for diagonal or asymmetric textures. It can also be useful to remove patterns that sometimes arise for models with U (or V) values of exactly 0 and 1.

<!-- -->

Wrap mode V  
Is the same as Wrap mode U, but it is for V values and the repeats are above and below.

<!-- -->

Magnif. Filter and Minif. Filter  
This specifies how to calculate the pixel values when the texture is enlarged or shrunken.

<!-- -->

  
The usual setting is, nearest and nearest , no mipmapping. This specifies that the value of the nearest pixel in the texture is used.

<!-- -->

  
bilinear and bilinear, no mipmapping is often for used transportation textures (E.g. Road) where you want to maximize details and to minimize “stair casing”. It specifies that several of the nearest pixels in the texture are to be used to calculate the pixel value. Using this setting will sometimes cause artifacts if a side of the triangle is right on the side of the texture. You may be able to fix this by using U,V values that are slightly greater than 0 or slightly less than 1.

<!-- -->

  
Note: Mipmapping is a way to encode all the different zoom levels into the same texture file. Mipmapping is not used by Maxis in SimCity, so a different texture file is used for each zoom level.

#### Anim

The order of entries in Anim is significant. If two objects coincide (have triangles that are in the same place on the same plane in space) the object that is further down the list will usually block out (hide) the parts that coincide on other object. This does not always work, and sometimes textures from both objects mix together in stripes. If the model will not be placed on a steep slope, shifting one object by 0.01m will prevent the stripes.

If an Anim entry has more than one line of numbers, each line is for a separate frame. The number of lines or frames, is specified in the Frame count field near the top of Reader’s window. The frames are used for animation, or are selected by different exemplar states.

##### Frame count

Note: removing frames in Reader v0.93 will corrupt the S3D.

Each ANIM group will have multiple lines if the frame count is greater than 1. One for each frame to be exact. Adding and removing groups is a separate procedure. However, it should be noted that using the 3DS functions on an S3D with multiple frames is a bad idea.

### Working with a Spreadsheet

Using a spreadsheet makes modifying an S3D much easier. Basically you copy tables from the S3D into the spreadsheet, and then use the spreadsheet to create modified tables that are copied back into the S3D.

For my examples I will use Microsoft Excel.

Suppose I want to move a model up by 10m. To do this, I copy all the values from the S3D’s Y column in Vert into column A in the spreadsheet. In the first row of another column (E.g. column C) I enter the formula =A1+10. Then I select the same number of rows in the column as there are rows in column A, and use Fill Down or CTRL-D to fill all the rows with the formula. I then copy the column from the spreadsheet back into the S3D’s Y column. As a result, all the Y values in the S3D will be increased by 10.

#### Select, copy, and paste in Reader

Unfortunately, using Reader to select a table, or copy or paste is different from most windows applications. (However, this depends on what OS you're using.)

To select a table in Reader you must first select the right/ bottom corner and then the left/top corner. Selecting the corners of the table in any other way will not work.

To copy a table in Reader you must use CTRL-C, and this must be done right after you select the table. If you do almost anything between selecting the table and typing CTRL-C, it will not work. The highlighting of the table does NOT mean that copy or paste will work.

To paste a table into Reader you must select the area that you will paste into and use CTRL-V. This area must be selected as described above (right/bottom then top/left), and you must paste as soon as you have made the selection.

Note: You can copy tables from reader to a text file, but it will be ugly.

In Reader, it is possible to copy or paste many groups at the same time. You simply open (make visible) all the groups you want, and select them all. When you paste into the spreadsheet there will be blank lines between each group. Anything that the spreadsheet puts in place of those blank lines will be ignored when you paste back into Reader.

Copying and pasting work in Vert, Indx, Prim. In Mats you can only copy or paste one field at a time. In Anim you can copy and paste rows and/or columns of the numbers, but copying or pasting multiple Anim names does not work correctly.

#### Spreadsheet Examples

To rotate a model, use the following mathematical formulae:

*Xrotated = X \* cos(angle) – Y \* sin(angle)* *Yrotated = X \* sin(angle) + Y \* cos(angle)*

And note that: *sin(0degrees) = 0, sin(90degrees) = 1, sin(-90degrees) = -1, sin(180degrees) = 0* *cos(0degrees) = 1, cos(90degrees) = 0, cos(-90degrees) = 0, cos(180degrees) = -1*

  
Xrotated = -Y 90degrees (counter-clockwise)

Yrotated = X

<!-- -->

  
Xrotated = Y -90degrees (clockwise)

Yrotated = -X

<!-- -->

  
Xrotated = -X 180degrees

Yrotated = -Y

radian = degrees \* π / 180

In excel, π is expressed as pi(), and angles are in radians; not degrees.

#### To rotate an S3D model by 30 degrees

Copy the X ,Y, and Z columns from Reader to the A, B, and C columns in the spreadsheet. You can rotate the points several groups at the same time, just open them and select them all when you copy/paste.

  
In E1 enter =A1\*cos(30\*pi()/180)-C1\*sin(30\*pi()/180)

In F1 enter =B1

In G1 enter =A1\*sin(30\*pi()/180)+C1\*cos(30\*pi()/180)

Select the area in the spreadsheet that includes E, F, and G, and that has the same number of rows as A, B, and C. Use CTRL-D to fill the table, then CTRL-C to copy it. Paste this back into X, Y, and Z in Reader. Press the Apply button and you are done.

Note that rotating the S3D created by BAT will usually not work because it makes the shadows look wrong.

#### To mirror image an S3D model

If you are only mirroring a part of the S3D, you must make sure that none of the Indx groups are used in both the mirrored and in the non-mirrored part.

Copy the X column from Reader in to the A column in the spreadsheet.

  
In C1 enter =-A1

Select the column C with the same number of rows that are in A. Use CTRL-D to fill column C and CTRL-C to copy it. Paste it back in to column X in reader.

The picture in Reader does not show this, but this operation will flip all the triangles so all the triangles that were visible will now be invisible, and all the triangles that were invisible will now be visible. Indx groups must be changed to correct this.

Empty the spreadsheet by selecting all the rows in A and C, then Right-click and select clear contents.

In Reader go to Anim find all the Indx groups that are associated with the points that you have changed (mirrored). Go to Indx and open only these groups. Copy them all, and paste them into the A, B, and C columns in the spread sheet.

  
In E1 enter =C1

In F1 enter =B1

In G1 enter =A1

This will swap the values of two columns. Select the area in the spreadsheet that includes E, F, and G, and that has the same number of rows as A, B, and C. Use CTRL-D to fill the table, then CTRL-C to copy it. Paste this back into the open Indx groups in Reader. Press the Apply button and you are done.

#### Rotating and flipping textures

A good way to rotate or flip a texture is to use the U, V values. (There is no need to change the Indx tables.) In this example I will assume that the texture will be centered (at (U,V) = (0.5,0.5)). This assumption is true for most traffic textures except highway textures.

Copy the U and V columns from Reader in to columns A and B in the spreadsheet.

To flip horizontally  
In D1 enter =1-A1

In E1 enter =B1

To flip vertically  
In D1 enter =A1

In E1 enter =1-B1

To rotate by 180  
In D1 enter =1-A1

In E1 enter =1-B1

To rotate by 90  
In D1 enter =B1

In E1 enter =1-A1

To rotate by -90  
In D1 enter =1-B1

In E1 enter =A1

Select the area in the spreadsheet that includes D, and E, and that has the same number of rows as A, and B. Use CTRL-D to fill the table, then CTRL-C to copy it. Paste this back into U, and V in Reader. Press the Apply button and you are done.
