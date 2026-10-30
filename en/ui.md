---
title: "UI"
description: ""
published: false
date: '2019-08-09T02:55:04Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2008-08-30T19:34:47Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**UI** stands for **User Interface**. These files control the visible interface you use in the game. UI's are basically a modified [XML](/xml) file. Most of the properties of the UI's are known, but the main IDs which link the functions of the various things together are not fully known yet.

The GID is different to GIDs on other files. Most UI files GID are 96A006B0. But if the UI is for a specific screen resolution then you put the screen resolution as the GID. Many of the Maxis UI files including the main mayor panel is designed for a 1024x768 or larger resolution but it doesn't fit inside a 800x600 window so a separate UI file was made and the GID of it was 08000600. Note the resolution is not converted to Hex.

## SimCity 4 UI Definition Files

[SimCity 4](/simcity-4) defines all of its user interface elements, or UI elements, through a text-based file similar to XML. SimCity 4 UI's are composed of legacy tags, which contain attributes defining the type of element, its look and behavior, etc. Legacies can have children, which contain more legacy tags defining child elements. SC4 UI files are not valid XML, but are very similar. It is known that these files also comprise the UI elements of newer Maxis games such as The Sims 2.

### Differences Between UI Files and XML Files

1\. In a UI file, a comment is denoted by a \# at the beginning of a line. In XML, a comment is denoted by a tag, contstructed as so: .

2\. In a UI file, legacy tags are not properly terminated. They have no closing tag or terminating bracket. UI LEGACY tags are simply closed by a \>. In XML, a tag must be terminated in one of the two following ways:

<LEGACY />  
`or`  
<LEGACY></LEGACY>

3\. In a UI file, there is no root tag. There may be more than one LEGACY tag at the root level:

<LEGACY>  
<CHILDREN>  
<LEGACY>  
</CHILDREN>  
<LEGACY>

In XML, you can only have one root element. The above code is invalid in XML, but this code would work:

<ROOT>  
` `<LEGACY>  
`   `<CHILDREN>  
`      `<LEGACY />  
`   `</CHILDREN>  
` `</LEGACY>  
` `<LEGACY />  
</ROOT>

4\. Attributes in a UI file are never bounded by quotes: <LEGACY clsid=GZWinGen>. In XML, attributes must be bounded by quotes: <LEGACY clsid="GZWinGen">.

The differences between XML and UI files poses a bit of a challenge, as a custom parser must be written to handle UI code, or a preparation parser must be written to convert UI code into valid XML. Once an UI file is valid XML, any normal XML parser should be able to generate a DOM in memory out of the UI code.

CHILDREN Tags are used when specifying controls that are inside other controls. For example, you may have a bitmap, and children tags below that which contain controls or trees inside the bitmap in-game.

LEGACY in a UI is a base control which contains other controls. If it contains no controls and is an end level class like text edit, it is not a legacy.

### UI Classes

SC4 UI files define user interface elements. This is done through attributes contained in LEGACY tags. The possible number of attributes is quite large, but not all attributes will always be used. First and foremost are the clsid, iid, and id attributes. These all define what kind of element a LEGACY tag is defining. Below is a list of known class id values for UI elements (this is the class id enumeration):

    Class ID Description
    ---------------- -----------------------------------------------
    GZWin        Base Control type which all subtypes inherit from.
    GZWinGen     Defines a UI window. This is a container control.
    GZWinText    Defines a simple text label.
    GZWinTextEdit    Defines a text edit box.
    GZWinBtn     Defines a push button.
    GZWinBmp     Defines a bitmap image.
    GZWinCustom      Defines a custom control.
    GZWinGrid    Defines a grid control.
    GZWinFlatRect    Defines a rectangle.
    GZWinSlider      Defines a slider control. (Like school capacity)
    GZWinCombo   Defines a combobox selection control (like MySim zodiac).
    GZWinListBox     Defines a listbox selection control.
    GZWinTreeView    Defines a treeview control.
    GZWinSpinner     Defines a spinner control. (Like tax adjusters).
    GZWinOutline     Defines an outline.
    GZWinScrollbar   Defines a scrollbar.
    GZWinFolders     Defines a Folder control.
    GZWinOptGrp      Defines an option Group control.
    GZWinTextTicker  Defines a Text Ticker Control.
    GZWinScrollbar2  Defines a scroll bar of an image style with different parameters.
    GZWinLineInput   Defines an Input control.
    GZWinFileBrowser Defines a File Browsing control.
    SC3WinGen    Defines a SimCity 3000 control window.

### UI Attributes

    Attribute   Type        Description
    --------------- --------------- ----------------------------------------------
    clsid       hex or enum     Defines the class of the control. Can be a hex
                    number or a class id. Where class ID's are non-hex they specify
                    that the control is standard. Where they are hex, as in some WinGen's
                    and WinCustom's, they specify that the overall control is specifically
                    defined in the EXE like with IDs, Except CLSID works for the control 
                    and its sub-elements as opposed to single Elements like text. 
                    Generally speaking a Hexid for a Wingen means a different control window
                    completely, so all of the sections from wingen onwards should not be displayed
                    all at once. IE in one UI file, you may find 5 different budget windows, identified
                    by hexid's for their clsid on a wingen.
        
    iid         enum        Defines the interface id for the control. Will
                    always be one of the class id enumeration values
                    with an I appended to the beginning. This is what
                    defines the type of interface the control is loaded as.

    id          hex         An id number in hex. This number identifies the data the control
                    deals with as defined in the EXE. It can be used as a sequence
                    as in 0000010b 20b and 30b to link three controls together, or
                    can be used as an id which can be linked to by the Button ID key
                    and Menu ID keys in the exemplar files. It can also simply be an ID
                    which identifies that control internally to the executable with no real
                    other result. ID may be exempted on non-interactive controls, 
                    or unused IDs can be created to facilitate new controls.

    area        rectangle   Defines the bounds of a rectangle that defines the controls area.
                                       Format: (x,y,width,height)

    fillcolor   color       Defines the default fill color of the control.
                       Format: (r,g,b)

    forecolor   color       Defines the foreground color of the control.
                       Format: (r,g,b)

    backcolor   color       Defines the background color of the control.
                       Format: (r,g,b)

    bkgcolor    color       Defines the background color of the control.

    caption     string      Defines the text used for the controls caption.

    captionres  hex         Defines the instance id of a localizable string
                    to be loaded from SimCityLocale.dat (or other location).

    transparent bool        Is the control transparent? Format Y|N
    showcaption     bool        Specifies weather the caption is shown for the control.
                                       Format: yes|no

    wrapcaption     bool        Specifies weather the control caption is wrapped.
                       Format: yes|no

    winflag_?   bool        Defines specific flags that affect the control.
                       Format: yes|no. See winflag section below.

    font        string      Specifies the font to use for the control text.

    autosize    bool        Specifies weather the control should be auto-sized.
                                       Format: yes|no

    sizable     bool        Specifies weather the control is sizable.
                       Format: yes|no

    movable     bool        Specifies weather the control is movable.
                       Format: yes|no

    tips        bool        Specifies weather the control has tooltips.
                       Format: yes|no

    tipsdelay   number      Defines the popup timeout for the controls tooltip.
                                       Format: milliseconds

    tipstimeout     number      Defines the disappear timeout for the controls tooltip.
                                       Format: milliseconds

    tipsflag    hex     Controls flag values in a 4 byte hex number related to the tips. Only 1 Defined.
                    0x01000000 Flag type 1. Just means is a standard tip.

    tipsoffset  position    Defines the offset the tip text appears at.
                       Format: (x,y)

    tipsres     hex     Defines the group and instance of the text for this tip. (hex gid,hex iid)
    tipstext    string      Defines the controls tooltip text.
    opaque      bool        Specifies weather the control is opaque.
                       Format: yes|no

    btnclicksnd     hex         Defines the group and instance id of the sound to play when the control is clicked.
                                       Format: {hex gid,hex iid}

    image       hex         Defines the group and instance id of the image to use for this control.
                                       Format: {hex gid,hex iid}

    colorfont?  color       The colorfont? lines define colors used for alternate font styles.
                                       Format: (r,g,b)

    toggle      bool        Defines weather the control is toggle-able. 
                       Format: on|off

    triggerondown   bool        Defines weather the control executes when pressed.
                       Format: on|off

    defaultkeys     bool        For a window, controls whether default control keys (such as escape to close) can be used.
    closevisible    bool        Is the close button visible?
    gobackvisible   bool        Is the back button visible beside close? (Revert to last state)
    minmaxvisible   bool        Is the minimize or maximize button visible?
    minmaxvalue number      Defines the minimum and maximum values of a slider. Format (min,max)
    blttype     enum        Blitting type. Format: tiled|normal|edge (stretched?)
    userdata    bool        An XML control used in UI windows for persisting data across multiple window sessions.
    closedisabled   bool        Is the close button disabled?
    gobackdisabled  bool        Is the back button disabled?
    minmaxdisabled  bool        Are the min/max buttons disabled?
    titlebar    bool        Window has a titlebar?
    outline     bool        Window has an outline?
    paint       bool        Draw the main window background? Format: Yes|No
    sidebar     bool        Does the window have a sidebar down left side? Format: Yes|No (extension of titlebar)
    imagerect   rectangle   Defines the rectangle that a bitmap may be used within. Format: (x,y,width,height)
    notify      bool        Notify other controls for this window of control information
    transparentbkg  bool        Defines whether the background of a control is transparent (mainly for bitmap controls)
    edgeimage   bool        For an image, repeat and stretch the image to the boundry areas?
    allowinsert     bool        For textedits Is inserting data allowed? Format: Yes|No
    allowundo   bool        Is Undo'ing/Cancelling allowed for input? Format: Yes|No
    singleline  bool        Is the data a single line only? Format: Yes|No
    initvalue   value       The Initial value of a control. Format: number or "value"
    highlightcolor  color       Defines color of control highlight. Format: (r,g,b)
    buttongutter    value       Defines the reserved space around the drop button of a combo box inside the control
    outlinecolor    color       Defines color of control outline. Format: (r,g,b)
    maxtext     number      Defines the max number of text chars allowed for control
    overwrite   bool        Overwrite Existing text (IE as Insert key Mode)? Format: Yes|No
    insertindex     value       For text edit controls, an unused control for directions on where in an array to
                    insert data (not confirmed).

    insertpos   number      unknown (textedit)
    notifyonreturn  bool        For Textedit, notify other controls in this window of textedit contents when return pressed
    notifyonchange  bool        For Textedit, notify other controls in this window of contents when contents are changed
    enableclipboard bool        For Textedits, are clipboard functions enabled, IE Cutting
    caretperiod     number      time in ms between cycles of the caret (blinking text insert cursor)
    caretcolor  color       Color of the text insert caret (cursor)
    maxundo     number      Maximum number of undo'able chars for the control (ctrl+Z)
    wrapped     bool        Is the text wrapped? (for noneditable text) Format Yes|No
    textoffsets     position    The position offset of the text on the control
                       Format (x,y)

    editable    bool        Is the Text Editable?
    hscrollbar  bool        Has a horizontal scrollbar (format: yes|No)
    vscrollbar  bool        Has a vertical scrollbar. Format: Yes|No
    selrule     number      grid cell selection rules. Enum: 0 - select whole column, 1 - select row, 2 select cell
    maxselcount     number      max number of selectable areas, ex: grid cells
    olinecolor  color       Defines an outline color. Format: (r,g,b)
    dcolwidth   number      Defines a column width.
    drowheight  number      Defines a column height.
    colhdrsz    number      Defines the size of the column header
    rowhdrsz    number      Defines the size of the row header
    textalign   value       Grid text alignment. Format: (#) - Grid standard for Vis basic is 0=left,1=right,
                    2=centre, 3 Default/General (text left, num right).

    textwrapping    value       Do grid text other than cells support wrapping or are they single line? 0,1=false,true
    fnone       bool        Is having an empty entry for a grid legal? (as notNull function in programming).
    fedit       bool        Is the grid data editable
    fhscroll    bool        Does the grid have a horizontal scroll
    fvscroll    bool        Does the grid have a vertical scroll
    fcolheading     bool        Does the grid have a column heading
    frowheading     bool        Does the grid have a row heading
    fcolgrid    bool        Is the column grid visible?
    frowgrid    bool        Is the row grid visible?
    finsmode    bool        Is insert mode used with data? IE overwrite data with data entering
    fopqbkgnd   bool        Is the grid background opaque?
    fdoutline   bool        Draw the main Outline for grid controls?
    fcellwrap   bool        Wrap grid cell data?
    fallownosel     bool        Allow no selection of a grid entry?
    ffixcolcnt  bool        Fixed Column count
    ffixrowcnt  bool        Fixed Row count
    fdpastlastcol   bool        Draw grid past last column
    fdpastlastrow   bool        Draw grid past last row
    fcelloverlap    bool        Grid cell data can overlap into other cells?
    fdrpdnmenu  bool        Data has drop down menu's
    fhlcelldata     bool        Highlight Cell data on hover?
    fdefault    bool        Obey grid defaults, or use manual settings
    fall        bool        Include all standard grid controls, IE scrollbars
    colgridclr  color       Grid column color. Format: (r,g,b)
    rowgridclr  color       Grid row color. Format: (r,g,b)
    wingridcol  values      Define Grid Column. 
                       Format : "columnorder,creationcount,columnwidth"

    btnupsnd    hex         Defines group and instance id of a sound played when a button is released. 
                       Format: {hex gid, hex iid}

    autonumber  bool        For spinners not connected to a textedit, controls whether the field is
                    an incremental integer field. A setting of no disables the spinner.

    autonumbercomma bool        For spinners not connected to a textedit, add commas to large values
    autonumbercurrency bool     For spinners not connected to a textedit, add $ to current values
    coloroutlineb   color       Defines a spinner bottom outline color. Format: (r,g,b) 
    coloroutliner   color       Defines a spinner right outline color. Format: (r,g,b)
    digits      as align    For spinners not connected to a text, determines the side of the spinners that text is on
    minmax      number      Minimum and maximum values of a spinner. format: (min,max)
    coloroutlinet   color       Defines a spinner top outline color. Format: (r,g,b)
    coloroutlinel   color       Defines a spinner left outline color. Format: (r,g,b)
    coloroutline    color       Defines a spinner outline color.
    stepsize    number      For spinners like taxes, incremental value of next step in either direction
    colorright  color       For rectangles, the color of the right side
    colorbottom     color       For rectangles, the color of the bottom side
    colortop    color       For rectangles, the color of the top side
    colorleft   color       For rectangles, the color of the left side
    displayroot     bool        For Tree View controls, view root item?
    displaynodeicons bool       For Tree View controls, display icons for tree nodes
    displaytreelines bool       For Tree View controls, display the tree lines (branches)
    multiselect     bool        Specifies if multiple selections are allowed.
    icongutter  number      For tree views, the pixel reserved space area around the items icons on the view
    rowheight   number      Defines a rows height.
    roottext    string      Text of the root item in a tree view when its displayed (in "" brackets)
    rootcolorforeground colour  Colour of the text for the root item in a tree view
    rootcolorbackground colour  Colour of the background for the root item in a tree view
    rootforegrounghilited colour    Colour of root item text for tree views when its selected
    rootbackgroundhilited colour    Colour of root item background for tree views when its selected
    rootexpanded    bool        For tree views, is the root expanded by default
    rootselected    bool        For tree views, is the root item selected by default
    rootfont    enum        For tree views, the font of the root item if it is displayed
    rooticon    hex     For a treeview display root icon?
    minmaxboxsize   number      For tree views, the size of the plus,minus icons for expansion of items.
    backgroundcolor color       For tree views, the background colour of the control surface
    highlightcolor  color       For tree views, the highlighted colour of selected items
    direction   enum        Direction of a slider. Format: horizontal|vertical
    initselection   number      For a control with selectable entries, the selected entry when it appears.
    combodownarrowrect number   Location of the combobox down arrow rectangle Format : (hor1,vert1,hor2,vert2)
    combodowncolor  colour      Colour of the combo box down/open control
    sunken      bool        For a list box, is the appearance sunken (recessed 3d)
    scrollbargutters number     For listbox's, the reserved space around the scrollbars. Format (hor,vert)
    shiftcaption    unknown     Unknown (button)
    sort        bool        Sort list items alphabetically?
    drop        bool        For listbox, drop edges in colour for 3d framed or layered look 
    colordark   colour      For outlines, the colour of an outline if it is not ontop of another control
    colorlight  colour      For outlines, the colour of an outline if it is ontop of another control
    node        number      For outlines, designates a node or end point for a line in an outline (hor,vert)
    comments    string      Earlier form of tips for controls. Comments on the control
    commentslmd     String      Same as above. Comments on Left mouse button Down
    commentsrmd     String      Same as above. Comments on Right mouse button Down
    commentslmu     String      Same as above. Comments on Left mouse button Up
    commentsrmu String      Same as above. Comments on Right mouse button Up
    commentsmm  String      Same as above. Comments on Middle Mouse button
    commentsku  String      Same as above. Comments on Keyboard up button
    commentskd  String      Same as above. Comments on Keyboard Down button
    pagesize    number      Defines the amount the scrollbar moves when you click on the bar (not the thumb or arrows)
    direction   enum        For scrollbars, the scrollbar type, vertical or horizontal
    linesize    number      Defines the amount the scrollbar moves when you click on the arrow (not the thumb or bar)
    linepagecount   number      Defines # of Lines per page and tot Page count for scrollbars. Format : (#oflines,#ofpages)
    listelements    string      List an element in a combo box, can be used multiple times, i.e. "1" etc.
    style       enum        The visual style of the control. Format: see table
    gutters     number      Reserved space around a control to make everything look cleaner.
                       Format: (hor,vert,hor1,vert1) in pix. First set are for top and left I believe
                    Second set should be for bottom and right. Second set are optional but used for buttons.

    autofit     solo        Autofit the control elements. No format. Used in texts
    maincaption bool        For an option group, show the main group caption?
    itemcaption     bool            For an option group, show the caption for each option?
    drawfill        bool    For an option group, colour fill the interior of the group edges? 
    labelfontcolornormal colour For an option group, the colour of the main group caption
    labelfontcolordisabled colour   For an option group, the colour of the main group caption if the group is disabled
    buttonfontcolornormal colour    For an option group, the colour of the radial and label if not hovered over
    buttonfontcolorhilited colour   For an option group, the colour of the radial and label if hovered over
    buttonfontcolordisabled colour  For an option group, the colour of the radial and label if the option is disabled
    outlinecolor    colour      For an option group, the colour of each side of the groups outline from top clockwise
    option          settings    Settings for an option in an option group, Format "Option#:Label:unk:unk:unk"
    optionmoveto    settings    For an option, distance in pixels from the top left of the group, Format" "Opt#:(hor,vert)"
    optionsetsize   settings    For an option, the size of said option and its labels area, Format" "Option#:(hor,vert)"
    autofilltype    enum        (option, manual or automatic)

### Added controls from August 27th 2004

    --GZwin
    imagetype
    fillcolor   colour      Defines the filled colour of the control window
    pos     hex     defines the x,y position of the Control window onscreen
    size

    --TextTicker
    message     string      The ticker message for a text ticker. A resource id could be used in place.
    frequency   number      The frequency of the text ticking across the screen for text tickers
    speed       number      Speed of moving text for a text ticker      

    --WinText
    dbgdrawarea hex     Defines the visible draw area of the text much like Photoshop creating a text box.
    defcolor    colour      Defines the text colour

    --Wintextedit
    passwordmode    bool        Enable hiding of characters in text edit as for passwords, "*" etc. 
    notifyonlostfocus bool      Notify textedit control on the user focusing on another control with a click
    vscrollimagerect rectangle  Defines the image rectangle for a textedits vertical scrollbar image
    vscrollimage    hex     Defines the group and instance of vertical scrollbar image for a textedit
    hscrollimagerect rectangle  Defines the image rectangle for a textedits horizontal scrollbar image
    hscrollimage    hex     Defines the group and instance of a horizontal scrollbar image for a textedit
    caretcolor  colour      Defines the colour of the Caret (the thing that shows where the typing cursor is). textedit

    --Winlistbox
    setlineontop    bool
    setlinevisible  bool

    --WinCombo
    combodownarrowrectimage hex Defines a combo boxes custom down arrow image. (gid,iid)

    --WinBMP
    alpha       bool        Older bitmap control value specifying whether an alpha can be used or not.

    --Scrollbar2
    thumbimage  hex     Defines
    containerimage  hex     Defines the contain
    arrowsimage hex     defines the image of the movement arrows (TID,GID,IID)
    increment   value       The increment of movement from moving the scrollbar based off the min max values etc
    pageoverlap value       When scrolling page by page, the overlap based on visible range from the last page
    visiblerange    value       Using the min and max values, the definition of a visible page from those values
    maxvalue    value       Defines the maximum value of the scrollbar. How far it can go
    minvalue    value       Defines the minimum value of the scrollbar
    value       value       The starting value or default value
    orientation enum        The direction of the scrollbar. horizontal or vertical

    --LineInput
    selection
    charlimit   value       Character limit for the input control
    caretpos    hex     x,y position of the caret (blinking position marker)
    fillalphahilite hex
    fillcolorhilite hex
    colorrbinside   colour      Colour of the right and bottom inside of a lineinput
    colorltinside   colour      Colour of the left and top inside of a lineinput
    colorrb     colour      Colour of the right and bottom outline of a lineinput
    colorlt     colour      Colour of the left and top outline of a lineinput
    filled      bool        Is the lineinput control filled (visible background) or not

    --Wingen
    divider     bool        An old form control no longer used that adds a divider to a control window
    bluebar     bool        An old form control no longer used that adds a blue bar to the control window side

    --WinFileBrowser
    filter      hex     Filter (par1,par2)
    backgroundtransparent bool  Is background transparent?
    backgroundimage enum        Background image?
                                       yes,no,outline

    backgroundcolor color       Colour of browser background
    drivelistsize
    backdirtext value       Text for the backdir button (..) normally
    highlightcolorbackground colour Color of background when item highlighted
    highlightcolorforeground colour Color of foreground item text when item highlighted
    columngridcolor colour      Color of main column grid
    columngridenabled bool      Enable column grid
    linegridcolor   colour      Color of line grid
    linegridenabled bool        Enable line grid for browser
    rowheight   value       Height of each item row
    extensioncolumnwidth value  Width of the column that displays file extensions
    iconcolumnwidth value       Width of the column that displays item icons.
    drivenamealignment enum     Enumeration for the type of alignment of the drive names on the browser
                                         right
                                         center
                                         left
                                         default
                                         unused

    drivenamebackgroundcolorhilited  colour  Drivename background color for hilgithed.
    drivenameforegroundcolorhilited  colour  Drivename Item Foreground colour for hilighted items.
    drivenamebackgroundcolordisabled colour  Drivename background colour for when a drivename is disabled.
    drivenameforegroundcolordisabled colour  Drivename foreground colour for when a drivename is disabled.
    drivenamebackgroundcolor         colour  Drivename background colour normal.
    drivenameforegroundcolor         colour  Drivename foreground colour normal.
    drivenamefont                    enum    Font to use for drivenames.
    fileextensionalignment           enum    Enumeration for the type of alignment of the file extensions on the browser.
                                                    right
                                                    center
                                                    left
                                                    default
                                                    unused

    fileextensionbackgroundcolorhilited  colour  Fileextension background color for highlighted.
    fileextensionforegroundcolorhilited  colour  Fileextension Item Foreground colour for highlighted items.
    fileextensionbackgroundcolordisabled colour  Fileextension background colour for when a drivename is disabled.
    fileextensionforegroundcolordisabled colour  Fileextension foreground colour for when a drivename is disabled.
    fileextensionbackgroundcolor         colour  Fileextension background colour normal.
    fileextensionforegroundcolor         colour  Fileextension foreground colour normal.
    fileextensionfont                    enum    Font to use for fileextensions.
    filenamealignment                    enum    Enumeration for the type of alignment of the file names on the browser.
                                                    right
                                                    center
                                                    left
                                                    default
                                                    unused

    filenamebackgroundcolorhilited  colour  Filename background color for highlighted.
    filenameforegroundcolorhilited  colour  Filename Item Foreground colour for highlighted items.
    filenamebackgroundcolordisabled colour  Filename background colour for when a drivename is disabled.
    filenameforegroundcolordisabled colour  Filename foreground colour for when a drivename is disabled.
    filenamebackgroundcolor         colour  Filename background colour normal.
    filenameforegroundcolor         colour  Filename foreground colour normal.
    filenamefont                    enum    Font to use for filenames.
    column#data                     value   Sets the containing data for filebrowsers for a column. sub # for col # and values are below:
                                               empty
                                               extension
                                               icon

    directorysort                   enum    Sets directory sorting type. Values below:
                                               bottomdescending
                                               bottomascending
                                               topascending
                                               topdescending
    filesortsecondary           enum    Sets secondary sorting type. Values below:
    filesortprimary             enum    Sets primary sorting type. Values below:
                                               byextensiondescending
                                               byextensionascending
                                               bynamedescending
                                               bynameascending
    defaultselectionextension  value    The default file extension selected
    defaultselectionname       value    The default selected item name
    defaultselectiontype       value    The default selection type. Select files, directories, or the back icon
    --file
    --dir
    --backdir
    defaultpath                value        Default file browsing path

    --Optgrp
    autofillsize    value
    backimage   hex     Option background image resource (gid,iid)
    captiontextresid hex        Main Option caption text resource id (gid,iid)
    buttonfont  enum        For option groups, set individual button fonts.
    labelfont   enum        For option groups, set group label font
    root        bool        
    sorted      enum        Sort Suboptions in specific way? If so, which?
                                        last
                                        first

    --Grid
    wingridrow  values      Define Grid Row. 
                    Format : "roworder,creationcount,rowheight"
    wingridcell
    fdgridoutline   bool        draw grid outlining?
    enablehdr   bool        Enable grid header?
    fontcolor   colour      Colour of the grid font

### Window Flags

Following are all the window flag attributes. These always are bool values, with possible values of yes or no. They are mostly self explanitory, and augment the behaviour of a control.

    winflag_visible - window is enabled/visible?
    winflag_enabled - window function is enabled?
    winflag_movable
    winflag_sizable
    winflag_sortable
    winflag_acceptfocus - control accepts mouse focus by click
    winflag_ignoremouse - ignore mouse commands
    winflag_pbuff - Pixel Buffer control? yes|no
    winflag_pbufftrans - Pixel Buffer Transfer. Write to a secondary buffer for flipping into place of current buffer as needed
    winflag_pbufferase - Erase Pixel Buffer before writing? yes|no
    winflag_pbuffvid - activate pixel buffering of video into memory for this control
    winflag_mousetrans
    winflag_alphablend - blend alpha layer into control - for transparent controls
    winflag_delayedplot - delay plotting of controls in the control window until after opening.
    winflag_premulalpha - premultiply alpha for control window

### Alternate Font Attributes

Following are all the possible alternate font color attributes. These are always color values.

    colorfontnormal
    colorfontdisabled
    colorfonthilited
    colorfontnormalbkg
    colorfontdisabledbkg
    colorfonthilitedbkg

### Known Enumerations

Some attributes have values that can be taken from an enumeration. An enumeration is a list of nonstandard values (i.e. standard values are string, number, hex)

    Align Enumeration
    -----------------
    left
    leftcenter
    center
    rightcenter
    right
    rightbottom
    righttop
    centerbottom
    centertop
    leftbottom
    lefttop

    Blit Type Enumeration
    ---------------------
    tiled
    normal
    edge

    Style Enumeration
    -----------------
    standard
    nofill
    fill
    raised
    sunken
    normal
    flat
    center
    left
    right
    top
    bottom
    label
    radiocheck
    flat
    toggle
    radio
    radiocheckall
    standardhilitefixed
    standardhilite
    noimage
    radiobtn
    checkbox
    togglebtnfixed
    togglebtn
    standardfixed
    standard
    outline3d
    outline3dex

### Possible Bool Values

`yes`  
`no`  
`on`  
`off`

## Lists of Standard Control Parts That Should Be Created With Each Control Type

Excluding clsid, iid, id, area, fillcolor, and winflags which are standard. Caption goes before winflags where applicable.

    GZWin
    ---
    winflag_visible,winflag_enabled,winflag_movable,winflag_sizable,winflag_sortable,winflag_acceptfocus,winflag_ignoremouse,
    winflag_mousetrans,winflag_alphablend,winflag_pbuff,winflag_pbufftrans,winflag_pbufferase,winflag_pbuffvid,caption,
    image,area,fill,gutters
    ---
    ------------------------
    GZWinGen 
    ---
    blttype,userdata,moveable,sizeable,defaultkeys,closevisible,gobackvisible,minmaxvisible,
    closedisabled,minmaxdisabled,titlebar,outline,paint,sidebar
    --- 
    ------------------------
    GZWinText 
    ---
    caption,align,notify,wrapped,opaque,forecolor,bkgcolor,gutters,textoffsets
    ---
    ------------------------    
    GZWinTextEdit   
    ---
    caption,editable,wrapped,hscrollbar,vscrollbar,outline,opaque,caretvisible,allowinsert,allowundo,
    singleline,initvalue,colorfontnormal,colorfontdisabled,colorfonthilited,colorfontnormalbkg,
    colorfontdisabledbkg,colorfonthilitedbkg,caretcolor,highlightcolor,outlinecolor,maxtext,gutters,
    overwrite,insertindex,insertpos,caretperiod,maxundo
    ---
    ------------------------    
    GZWinBtn    
    ---
    image,colorfontnormal,colorfontdisabled,colorfonthilited,colorfontnormalbkg,colorfontdisabledbkg,
    colorfonthilitedbkg, toggle, triggerondown,showcaption,fill,autosize,wrapcaption,shiftcaption,tips,
    tipsdelay,tipstimeout,style,gutters,tiptext,tipoffsets,tipflag,align,btnclicksnd
    ---
    ------------------------    
    GZWinBmp    
    ---
    image,imagerect,notify,transparentbkg,edgeimage
    ---
    ------------------------    
    GZWinCustom     
    ---
    caption
    ---
    ------------------------    
    GZWinGrid   
    ---
    fontcolor,textalign,textwrapping,gutters,selrule,maxselcount,olinecolor,dcolwidth,drowheight,colhdrsz,
    rowhdrsz,fnone,fedit,fhscroll,fvscroll,fcolheading,frowheading,fcolgrid,frowgrid,finsmode,fopqbkgnd,
    fdoutline,fdgridoutline,fcellwrap,fallownosel,ffixcolcnt,ffixrowcnt,fdpastlastcol,fdpastlastrow,
    fcelloverlap,fdrpdnmenu,fhlcelldata,fdefault,fall,colgridclr,rowgridclr,wingridcol,wingridcol
    ---
    ------------------------    
    GZWinFlatRect   
    ---
    colorleft,colortop,colorright,colorbottom,style
    ---
    ------------------------    
    GZWinSlider     
    ---
    minmaxvalue,direction,image,initvalue
    ---
    ------------------------    
    GZWinCombo  
    ---
    font,fill,editable,outlinecolor,initselection,combodownarrowrect,combodowncolor,buttongutter,gutters,listelement (usually multiples)
    ---
    ------------------------    
    GZWinListBox    
    ---
    vscrollbar,hscrollbar,font,colorfontnormal,colorfontdisabled,colorfonthilited,highlightcolor,outlinecolor,sunken,
    outline,scrollbargutters,gutters,sort,drop,initselection
    ---
    ------------------------    
    GZWinTreeView   
    ---
    displayroot,displaynodeicons,displaytreelines,multiselect,icongutter,rowheight,minmaxboxsize,backgroundcolor,
    highlightcolor,roottext,rootcolorforeground,rootcolorbackground,rootcolorforegroundhilited,rootcolorbackgroundhilited,
    rootfont,rootexpanded,rootselected
    ---
    ------------------------    
    GZWinSpinner    
    ---
    caption,image,outline,fill,autonumber,autonumbercomma,autonumbercurrency,initvalue,minmax,stepsize,
    coloroutlinel,coloroutlinet,coloroutliner,coloroutlineb,digits,align,colorfontnormal,colorfontdisabled,
    colorfonthilited,gutters
    ---
    ------------------------    
    GZWinOutline    
    ---
    colordark,colorlight,style,node (multiples usually)
    ---
    ------------------------    
    GZWinScrollbar  
    ---
    minmaxvalue,direction,pagesize,linesize,linepagecount,image,initvalue
    ---
    ------------------------    
    GZWinFolders    
    ---
    font,listelement
    ---
    ------------------------    
    GZWinOptGrp     
    ---
    caption,maincaption,itemcaption,drawfill,outline,gutters,labelfontcolornormal,labelfontcolordisabled,
    buttonfontcolornormal,buttonfontcolorhilited,buttonfontcolordisabled,outlinecolor,initselection,autofilltype,
    option,optionmoveto,optionsetsize
    ---
    ------------------------    
    SC3WinGen
    ---
    ---
    ------------------------
    GZWinTextTicker
    ---
    message,frequency,speed
    ---
    ------------------------
    GZWinScrollbar2
    ---
    orientation,minvalue,maxvalue,visiblerange,pageoverlap,increment,value,containerimage,thumbimage
    ---
    ------------------------
    GZWinLineInput
    ---
    selection,charlimit,caretpos,fillalphahilite,fillcolorhilite,colorrbinside,colorltinside,colorrb,colorlt
    outline3dex,outline3d,filled
    ---
    ------------------------
    GZWinFileBrowser
    ---
    filter,backgroundtransparent,backgroundimage,backgroundcolor,drivelistsize,backdirtext,hilightcolorbackground
    ,hilightcolorforeground,columngridcolor,columngridenabled,linegridcolor,linegridenabled,rowheight,extensioncolumnwidth
    ,iconcolumnwidth,drivenamealignment,drivenamebackgroundcolorhilited,drivenameforegroundcolorhilited
    ,drivenamebackgroundcolordisabled,drivenameforegroundcolordisabled,drivenamebackgroundcolor,drivenameforegroundcolor
    ,drivenamefont,fileextensionalignment,fileextensionbackgroundcolorhilited,fileextensionforegroundcolorhilited
    ,fileextensionbackgroundcolordisabled,fileextensionforegroundcolordisabled,fileextensionbackgroundcolor
    ,fileextensionforegroundcolor,fileextensionfont,filenamealignment,filenamebackgroundcolorhilited
    ,filenameforegroundcolorhilited,filenamebackgroundcolordisabled,filenameforegroundcolordisabled,filenamebackgroundcolor
    ,filenameforegroundcolor,filenamefont,column2data,column3data,column1data,default,directorysort
    ,bottomdescending,bottomascending,topascending,topdescending,filesortsecondary,filesortprimary,defaultselectionextension
    ,defaultselectionname,defaultselectiontype,defaultpath

    control+lefttodo
    grid 2, textedit 3, button 1, opt 5, winflag 3, win 2, lbox 2, sb2 2, lineinput 3, browse 2 

## Unknown Properties

There are 24 remaining unknown properties of UI files:

`winflag_sortable (common)`  
`winflag_mousetrans (common)`  
`allowinsert (textedits)`  
`insertindex (textedits)`  
`insertpos (textedits)`  
`fnone (grid)`  
`shiftcaption (button)`  
`option (optgrp) - defines this option's information`  
`autofilltype (optgrp) - for filling the whole option control`  
`imagetype`  
`size`  
`setlineontop`  
`setlinevisible`  
`thumbimage`  
`containerimage`  
`selection`  
`fillalphahilite`  
`fillcolorhilite`  
`filter`  
`drivelistsize`  
`autofillsize`  
`root`  
`wingridcell`  
`winflag_container`
