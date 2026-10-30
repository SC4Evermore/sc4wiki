---
title: "Type Group Instance"
description: ""
published: false
date: '2021-05-05T16:18:06Z'
tags: ["Modding"]
editor: markdown
dateCreated: '2008-11-07T19:41:33Z'
---

The **Type Group Instance**, officially **Persistent Resource Key** or **GZPersistResourceKey**[^1], and typically abbreviated **TGI**, is the sorting format of the Database Packed File (DBPF) archive, and is used to identify, reference, and link files within [DBPF](/dbpf) files. A file's TGI consists of three, eight-digit [hexadecimal](/hexadecimal) numbers, the [Type ID](/type-id), [Group ID](/group-id), and [Instance ID](/instance-id), respectively. As TGI's are relatively unique to a particular object, they are the preferred method for referencing game objects, which might have multiple names in a variety of languages or naming conventions. Additionally, objects sometimes have very similar names, making the TGI an ideal way to differentiate between the two.

While efforts are generally made to prevent two objects from having the same TGI, this still sometimes occurs, and can cause conflicts or bugs in the game, particularly when it happens with buildings, props, or textures. Sometimes, particularly in the case of mods, it is desired to give an object the same TGI as another, so that one will override the other. Typically, this involves creating a mod that has the same TGI as a Maxis object that came with the game, so that the custom mod will overwrite the default settings.

An object's TGI is commonly written in full as:

`AAAAAAAA BBBBBBBB CCCCCCCC`

where "AAAAAAAA" is the Type ID, "BBBBBBBB" is the Group ID, and "CCCCCCCC" is the Instance ID.

During certain modding operations, a [TGI File](/tgi-file) may be generated. These are not native to the game and serve no purpose in modding SC4.

See also:

- [InstanceFormats](/instanceformats)

## References

[^1]: SC4D User Speeder, ""TGI" has a official name ...the name of TGI is GZPersistResourceKey", 22nd January, 2016 [1](https://www.sc4devotion.com/forums/index.php?topic=17302.msg504536#msg504536)
