---
title: "Shortcut Parameters"
description: ""
published: true
date: '2019-08-09T09:35:20Z'
tags: ["Gameplay", "The Game", "Customizing the Game"]
editor: markdown
dateCreated: '2008-10-08T04:02:12Z'
---

There are a number of parameters that you can preset before game launch to allow for multiple advanced options that the game normally does not support through its User Interface. To use these parameters you must edit your game shortcut or the Launch Parameters field in Steam.

## Retail - The Shortcut File

There will probably be a game shortcut on your desktop, it should look something like this:

<figure>
<img src="/_files/images/sc4-shortcut.png" title="SC4_Shortcut.png" />
<figcaption>SC4_Shortcut.png</figcaption>
</figure>

If you cant find one on your desktop, there is one in your My Programs/Maxis/SimCity 4/ menu.

Right click on that icoi and select properties. This window will open:

<figure>
<img src="/_files/images/shortcut-properties.jpg" title="Shortcut_Properties.jpg" />
<figcaption>Shortcut_Properties.jpg</figcaption>
</figure>

Add your parameters to the end of the Target box

## Steam - The Launch Parameters field

The images used here will be from the game The Elder Scrolls V: Skyrim and using a custom skin, however the workflow is exactly the same.

Right Click SimCity 4 Deluxe in the Library Tab and select Properties.

<figure>
<img src="/_files/images/steamlaunchoptions1.jpg" title="SteamLaunchOptions1.jpg" />
<figcaption>SteamLaunchOptions1.jpg</figcaption>
</figure>

In the General Tab, click the "Set Launch Options" button.

<figure>
<img src="/_files/images/steamlaunchoptions2.jpg" title="SteamLaunchOptions2.jpg" />
<figcaption>SteamLaunchOptions2.jpg</figcaption>
</figure>

Add your parameters to the text field, then click OK.

<figure>
<img src="/_files/images/steamlaunchoptions3.jpg" title="SteamLaunchOptions3.jpg" />
<figcaption>SteamLaunchOptions3.jpg</figcaption>
</figure>

Close the properties window.

## Simple Parameters

These are easily used parameters for use in many situations.

### No Intro

`-intro:off`

This simply turns the intro videos off, and takes you straight to the game (via one splash screen)

### Windowed Mode

`-w`

Starts the game in a window. <!-- unconverted template: note -->

## Video Settings

### Screen Resolution

`-r[a]x[b]x[c]`

Sets the screen resolution to \[a\] pixels wide by \[b\] pixels high, with a bit-depth of \[c\]. <!-- unconverted template: note --> <!-- unconverted template: note -->

### Custom Resolution

`-CustomResolution:enabled`

Allows non 4:3 aspects to be used with the [-r](#screen-resolution) command.

### Rendering Mode

`-d:[renderer]`

Forces the game to use the specified Renderer mode. Valid values are Software and DirectX (The Hardware option in the Graphics Options menu in-game).

There is an OpenGL mode, however forcing the game into this mode is highly discouraged due to its buggy and unfinished state.

## Audio Parameters

These properties affect the sounds made by the game.

`-audio:off`

Turns all the audio output off

`-sound:off`

This will run the game with no sound, which is useful for troubleshooting audio issues.

`-music:off`

This will run the game with no music, which is useful for troubleshooting audio issues.

## Processing Options

`-AllowMultipleInstances`

This allows you to launch additional game instances after the first one. By default, an attempt to run the game more than once will merely call forth the first instance of the application.

`-BackgroundLoader:on/off`

This enables or disables the background model loading system. Normally, when you switch the view zoom or rotation the application loads only the visible objects first and makes a background task of loading the additional models. This allows the game to be more responsive during view changes, but it has the side effect of slowing down the game for the next few seconds or minutes.

`-CPUPriority:low`

This specifies that the game set its base process priority to low instead of normal. This is useful for having the game run side-by-side with other applications and have it not take too much processing time away from the other applications.

## Other

### User Dir

`-UserDir:[path]`

Specifies the directory where the users game directory is. If the default subdirectories of "Regions\\, "Plugins\\, and "HTTPCache\\ arn't found, then it creates an instance of, (in the case of Regions, it copies the default set over). The default game data directory defaults to being the same directory as the game installation directory. Quotes are necessary if the path name has spaces. Make sure there is a "\\ on the end of your path or it creates directories like "testPlugins\\ and "testRegions\\

### Language Settings

`-l:language`

This specifies the language to run the game in. The game can only run in a language if the resource data for that language is present in the application's data set. Valid languages are: English, German, UK English, Traditional Chinese, and Japanese.

## See Also

- [Parameters Tutorial](/tutorial/zztoken3zz) by
- ...
