---
title: "LUADefs"
description: ""
published: true
date: '2019-08-04T05:40:51Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-09T21:25:53Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**LUA Definitions**, blocks 22508,26328,40384,5652. This specification covers how [LUA](/lua) scripts in [SimCity 4](/simcity-4) define variables.

## Specification

Definitions scripts are softcoded. This means each type of definition used may depend on other types of definitions coded elsewhere in the LUA's. It is necessary to go right up the file tree of *dofiles* in order to find the originally used tables.

### Starting Block

    dofile("filename.lua")
       -- The usual dofile includes before parsing

    (Optional if statements)

    (Additional functions, if any)

If the optional *if* statements exist in the Starting Block, then the LUA file is terminated with an End Block since the whole file is inside the *if* statement. They abide by LUA standard Specs.

### Definition Block Types and Definition Types

There are 5 ways of defining variables that will be covered here. Of course, other methods exist in LUA, but these ones are used regularly in [SimCity 4](/simcity-4).

#### Type 1

This table has all things defined within the brackets. This is convenient sometimes due to less typing required. A call would look like "Advisor_anim_types.NEUTRAL"

    advisor_anim_types = 
    {
      NEUTRAL = 0,
      HAPPY = 1,
      ATTENTION = 2,
      ALARMED = 3
    }
    make_table_const (advisor_anim_types )

#### Type 2

These two statements define the different animations for moods for the new adviser head HR. The hex2dec value is the instance for a [S3D](/s3d) file.

    hr = advisor_heads : new_record(advisor_ids.TRANSPORTATION, advisor_genders.M)
        -- Create variable HR which is a new adviser head record, shown here is the transportation adviser of male gender.

    hr[advisor_anim_types.NEUTRAL] = hex2dec("2a42b530")
    hr[advisor_anim_types.HAPPY] = hex2dec("2a42b532")

#### Type 3

These definition types create variables with functions as their value. Therefore each time the script is called, the function is executed and the variable is recalculated by using the function.

    game.trend_slope = function (trend_type, period_in_months) return 0 end
        -- Returns a trend value between (-100, +100) for the period of time (see game_trends for trend types).
    game.trend_value = function (trend_type, num_months_ago) return 0 end
        -- Returns a value the trend variable had 'num_months_ago'.

#### Type 4

This type of definition script is almost like the first one. It would seem that they can be used back and forth as required.

    advice_types = {}
    -- on C++ side this will correspond to advisor ID 
      advice_types.NULL = 0
      advice_types.MYSIM = 1
      advice_types.UTILITIES = 21
      advice_types.HEALTH_EDUCATION  = 22
    -- This table has to be extended at the end
    make_table_const (advice_types)

#### Type 5

GUID Definitions such as this may exist outside a bracket like other definition types. It seems they must have an end statement at the end of the file though. The GUID is the instance for a UI file.

    GUIDExemplars = "0xa079ce1b"
    GUIDCivicBuildings = "0x07bddf1c"
    GUIDResidentialBuildings = "0x67bddf0c"
    GUIDCommercialBuildings = "0x47bddf12"

### End Block

The End Block only exists if there was an opening *if* statement in the Starting Block.

    end
