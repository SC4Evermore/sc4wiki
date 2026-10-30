---
title: "LUA"
description: ""
published: false
date: '2019-08-09T02:54:58Z'
tags: ["File Formats/SC4", "Modding", "MTS2"]
editor: markdown
dateCreated: '2009-01-06T16:54:47Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**LUA** is an imperative programming language, designed in 1993 by Roberto Ierusalimschy, Luiz Henrique de Figueiredo, and Waldemar Celes, members of the Computer Graphics Technology Group (Tecgraf) at PUC-Rio, the Pontifical University of Rio de Janeiro, in Brazil. "Lua" means "Moon" in Portuguese. Lua is used in [SimCity 4](/simcity-4) for the generation of help texts, creation of rewards, defining [U-Drive-It](/u-drive-it) missions, and other types of codes.

More information about Lua can be found on the [official site](http://www.lua.org/) and on [Wikipedia](http://en.wikipedia.org/wiki/Lua_(programming_language)).

## Use in SimCity 4

Lua has many uses in SimCity 4, as mentioned above. The exact format used can vary depending on the use. The formats below are courtesy of [Karybdis](/people/karybdis).

Instance by: CRC24Polynomial = 0x01864cfb, CRC24Seed = 0x00b704ce, return (CRC24(from, false) \| 0xFF000000)

The types of LUA files are:

- [Advice LUA's](/luaadvice)
- [Advisor Definitions Script](/luaadvisors)
- [LUA Definitions](/luadefs)
- [Mission LUA Files](/luamission)
- [LUAObject](/luaobject)
- [System LUA Files](/luasystem)
- [Tutorial Scripts](/luatutorials)

## Binary LUA

The following format is for binary Lua scripts, and was developed by [Quaxi](/people/quaxi).

Here are the first things known about the .objLua and .globalObjLua:

### General Format

        DWord: 1b 4c 75 61   (ID)
        Byte: Version    
        16-Bytes: Header
            ---> Root "Function Block"

### Function Block

        Dword: Character count n
        n-Byte: Name of the Function (null terminated)
        5-Byte: unknown
        Byte: argument Count
        Byte: unknown
        Byte: stack Size
        
        12-Byte: 00

        4-Byte: constant counter 
            ---> Loop Constant Block
        
        4-Byte: functions counter
            ---> Loop Function Block

        4-Byte: instruction counter
            ---> Loop Instruction Block

### Instruction Block

(a=Operand a, b=Operand b, c=Operand c, o=Opcode):

        Dword: aaaa aaaa bbbb bbbb bccc cccc ccoo oooo    

This Document lists the available opcodes: <http://www.tecgraf.puc-rio.br/~lhf/ftp/doc/sblp2005.pdf>

### Constant Block

        Byte: ConstantType
            ----> Constant Data

### List of Known Constant Data Types

`0x00 = Empty, Null -  This seems to mark an empty block`  
`0x03 = Number`  
`          DWord: Unknown`  
`          DWord: Unknown`  
`0x04 = Strings`  
`          DWord: Length n of the following PString`  
`          n-Bytes: Instruction Name, null-terminated`
