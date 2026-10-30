---
title: "LUAAdvisors"
description: ""
published: false
date: '2019-08-04T05:40:51Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-09T22:19:59Z'
---

The **Advisor Definitions Script** defines the Advisor Details. The [TGI](/tgi) for this file is *0xca63e2a3,0x4a5e8ef6,0xff456218*.

## Specification

This [LUA](/lua) file contains a starting block, followed by the Main Advisor Table, which includes all of the advisor definitions.

### Starting Block

The file begins with the usual round of *dofile* includes.

    dofile("filename.lua")

This is immediately followed by a template that is used for the advisor definitions later in the file.

    advisor_base_template = create_template
    ({
       class_id = 0,
       id = 0, 
       advice_type = 0,
       caption = "",
       name = "",
    })

### Main Advisor Table

The next section of the file is the beginning of the main advisor table. This table includes the definitions for all of the advisors in the game. It begins by resetting the advisor count to zero, then defining some functions to enable the use of the above template in the following definitions.

    advisors = {n = 0}
      -- Set current advisor number to 0 to begin file.

    function advisors : new (init_table, base_table, flat)   -- Function definition
       local t = advisor_base_template : new (init_table, base_table, flat)
       local i = getn(self) +1
       self[i] = t               -- Add the table to the main advisors' repository
       self . n = self . n + 1   -- Update the table count
       return t
    end

This is then followed by two sections, the **department_advisor** and **mysim_advisor** sections, which themselves contain the actual advisor definitions for each of the two types of advisors. Each section begins with an opening category definition. Here the *mysim_advisor* is shown as an example:

    mysim_advisor = advisors : new     -- Creates a new advisor type for use in the definitions to follow.
    ({
       class_id = hex2dec('4a1dbbbf'), -- Class ID for this advisor type.
       id = advisor_ids.NULL,          -- This one will be ignored by the game.
    }, nil, nil)                       -- Unused since this is creating a type.

Following the category definition is a series of entries for each of the advisors of that type. The example below shows the format of these entries.

    advisors : new (
    {
       class_id = hex2dec('6a5f8755'),           -- Class ID used in-game for the advisor.
       id = advisor_ids.HEALTH_EDUCATION,        -- Type from definitions LUA.
       advice_type = advice_types.HEALTH_EDUCATION, -- Type from LUA.
       caption = "text@aa49638a Health & Education Advisor", -- Text of Advisor title.
       name = "text@0a75f82b",                   -- Text of Advisor Name.
    }
    , department_advisor                         -- Advisor type as defined in above category definition,
    ,1)                                          -- Flat value, model treated as flat model or not.
                                                    No real noticeable difference from changing this.

The file simply ends after the last advisor definition.
