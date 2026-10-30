---
title: "LUATutorials"
description: ""
published: true
date: '2019-08-04T05:40:52Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-15T22:00:30Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

One type of [LUA](/lua) file found in [SimCity 4](/simcity-4) are the **tutorial scripts**. The tutorial script LUA files themselves are located at [Instance IDs](/instance-id) of: *fffe38d1*, *ffc346e2*, *ffa99857*, *ff2c44c4*, *ff27e999*, *ff11b8f0*. Tutorials must be registered in the **Tutorial Registry**, which has Instance ID *ff7d91e7*, and contains a section at the bottom listing the registered tutorials. The format of the registry is:

`tutorial_registry: add_tutorial(hex2dec('abfad020'), 0, 'timbuktu')`

Where the ID is the Tutorial IID, 0 is the order of tutorials, and timbuktu is the region directory the tutorial takes place in. There are five of these in the game, and one obsolete one. The five active tutorials have IID's of: *abfad020*, *ea5d6dc8*, *0bfdb71b*, *cc02d3a3*, *2c12d0e9*. Note that these IID's are for nested [DBPF](/dbpf) files within simcity_1.dat, not the tutorial scripts themselves.

## Specification

The tutorial scripts begin with a series of definitions and functions in order to set the properties for how various things in the tutorials are determined. These only need to be defined once. The other two scripts simply call on these definitions in order to determine things.

All tutorials are made based on **steps**. A step is an independent thing that you do inside a tutorial. When you complete what is requested you move onto the next step. Tutorials consist of a series of these steps followed by an ending block. Below is an example step and ending block with descriptions where possible.

### Start Block

This block exists in the Primary Tutorial only.

    tutorialtasks = { n = 0 }       -- Primary Tutorial

    tutorial_number_index = { }     -- Set Tutorial Index

    tutorial_decal_color_type = {}  -- Decal table
       tutorial_decal_color_type.DECAL_YELLOW = "selection_yellow"
       tutorial_decal_color_type.DECAL_GREEN = "selection_green"

    tutorial_file_guids = {}
    tutorial_file_guids[1] = "0x8a5b7a6c"
    tutorial_file_guids[2] = "0xea5d6dc8"

    tutorial_zone_type = { }
       tutorial_zone_type.kZoneTypeUndefined = 0
       tutorial_zone_type.kZoneTypeLowDensityResidential = 1

    tutorial_building_type = {}
       tutorial_building_type.kOilPowerPlant = "0x1f420000"
       tutorial_building_type.kCoalPowerPlant = "0x1f4d0000"

    tutorial_dispatch_type = {}
       tutorial_dispatch_type.kDispatchTypePolice = 0
       tutorial_dispatch_type.kDispatchTypeFire = 1

    tutorial_network_type = { }
          tutorial_network_type.kRoad = 0
          tutorial_network_type.kRail = 1

    tutorial_buttons = {}
       tutorial_buttons.kButtonDemolish = "0xe999c820"
       tutorial_buttons.kButtonDezone = 0
       tutorial_buttons.kButtonLowDensityResidential = "0x01"

    tutorial_base_task_action = 
    {
       which_function = 0,
       startX = 0,
       startZ = 0,
       endX = 0,
       endZ = 0,
       guid = 0,
    }

    tutorial_function_index = {}
       tutorial_function_index.UNDEFINED = 0
          -- These are functions that ask users to do some task
          -- and check if users succeeds or not.
          -- ASK_TO_ZONE_AND_CHECK = 1,
       tutorial_function_index.ASK_TO_ZONE_AND_CHECK = 1

    -- All functions are designated in this block.
    -- Functions may be called from inside a command or may be inside any step independently.
    -- For example,

    function set_camera(object, XCoord, ZCoord) 
       object.cameraX = XCoord;
       object.cameraZ = ZCoord;
    end

### Step Block

    -- Step # ---

    a = tutorial_create_task("0a39f624")
       -- Create step with this GUID.
    a.task_action = tutorial_check_button_clicked_no_arrow(tutorial_buttons.kButtonTerraform)
       -- Task which is based off a defined function from above.

    tutorial_button_set(a,      -- Set buttons based from the tutorial button function
      tutorial_buttons.kButtonTerraform,
      tutorial_buttons.kPuckButtonGod,
      tutorial_buttons.kButtonZoomIn,
      tutorial_buttons.kButtonZoomOut)

    a.zoomLevel = 0;     -- Zoom level for step
    set_camera(a,68,60)  -- From defined function above

    a.instruction_msg = [[text@0x8a5ae472]]
       -- Locale IID for text. Define afterwards for lack of data possibilities if you want.
    a.try_again_msg = [[text@ea4ad695]]
       -- Locale IID for text. Define afterwards for lack of data possibilities if you want.
    a.congratulation_msg = [[text@8a5adc16]]
       -- Locale IID for text. Define afterwards for lack of data possibilities if you want.

### End Block

    tutorial_number_index[2] = tutorialtasks.n+1  -- Tutorials completed (now 2).
    print ("second tutorial script")              -- Order of this script in the tutorial list.
    print (tutorial_number_index[2])              -- Location of this tutorial in index (second).
    dofile("tutorial_tasks3.lua")                 -- Next tutorial call.
    --print(tutorialtasks[1].task_action) 
    print(tutorialtasks[1].target_buttons[1])     -- Print first target button.
    --print(tutorialtasks[3].target_buttons[1])
    --print(tutorialtasks[5].target_buttons[1])
    --print(tutorialtasks[4].task_action.target_guids)
