---
title: "SGR"
description: ""
published: true
date: '2019-08-09T02:55:02Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2012-09-07T23:24:12Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

Full specification to current knowledge for the **SimCity Graphics Rules (SGR)** file type.

    #

    #<
    text group
    >#

    set <variable> <value>

    optiongroup $groupname
        option $optionchosen(i.e. low, med, high, off)
            property <variable> <itemvalue> (itemvalue is a bool, int, or $variable )
    end

    partialRule "groupname"

      rule (optional mainrule)
       stringmatch <string to match, ie osVersion> "<stringval>" (optional for mainrule)

       rule "<quality> <groupname> [detail,power]" (groupname is something like memory, etc.)
          atLeast(or atMost) <memory,cpuspeed,videoMemory>
          (optional string) hasNo <type, ie hardwareDriver>
          option $optiontype $quality (low, med, high etc.)
          (an optional property can go here with or instead of option)
       end
      end (optional for mainrule)
    end

    vendor "vendorname" <id's this vendor uses, 0x#### 0x#### etc>
        card <cardid 0x####> "name to use for card"
    end

    sinclude "file.sgr"

    ----------------------------

    In the area above, () brackets contain user notes. They are not part of the specification.
    [] brackets indicate a conditional setting which may or may not be used depending on what your  action is.
    <> brackets indicate a substitution bracket, take out the <> brackets and replace them with an example of what it says to use inside them.
    "" brackets indicate a string value that should be contained in quotes when used.

    #'s make everything after them on that line be excluded from the code.
    #<># : This is a block quote out. Anything for however many lines between the two brackets will be excluded from being gone over by the code.
    Set is a standard definition for a variable. Set variable to value.

Optiongroup, partialRule, and vendor are all maingroups. That means that there will probably be more groups within them defining more specific parts of that area. An optiongroup is for in-game options, as are the options and properties set from within them. You declare what the property will be based on the option chosen using integers, Boolean values, or more variables that are declared at that point. Vendor is specifically for video card vendors.

Rule is a submaingroup meaning that it further divides the areas above. Rule is only used in conjunction with partialRule however.

All maingroups and submaingroups are terminated by an end statement "end".

Sub-directives such as Option (used with optiongroup maingroups), stringMatch, atLeast, atMost, and hasNo are all for defining what happens based on specific criteria, for instance if this option is set to medium, do the line after this option or the number of lines after this option. Another example is if the cpuSpeed of this computer is atLeast this high, do this.

Property, option (used with rule maingroups), and card, are types of results. They say what happens based on the criteria set in the sub-directive. If if this rule is met accurately and the cpuspeed is say 2000, then set this option to medium. "option \$cars \$medium" for instance. This type of option declaration may then be reused in an optiongroup setting.

Finally sinclude statements simply tell the code to include this file while working. This may be useful for definitions.
