---
title: "LUAObject"
description: ""
published: false
date: '2019-08-04T05:40:52Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-15T21:07:37Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

[LUA](/lua) files relating to sprites and [automata](/automata) are covered by certain principles. They may contain any of the following.

## Specification

### File Block

    (Helper Data)
       -- This data, such as a function or an if command, are either helpers or control agents for the file.
          For example, a file failing an if command will not execute.

    dofile("filename.lua")
       -- This means that filename.lua must be parsed before this script is executed.
          This command may be repeated for other files. The dofiles look for hashed IIDs representing the name.

### Automata Group

The Automata Group is used for files containing automata.

    automata_group.pedestrian = -- Name of the group to create
    {
      _parent = (data)          -- The parent data to this automata group if any.
                                   This causes inheritance of properties.
      group_id = "0x8a1e1740",  -- Occupant group as defined in the LUA's.
      anims = {                 -- Animations for this automata to use, if any.
        walk = 0,
        wait = "0x0C",
        woohoo = "0x07",
        whoop = "0x0A",
        hop_clap = "0x0B",
        clap = "0x09",
        booyah = "0x08",
        panic_run = "0x0D",
        tantrum = "0x06",
        reject = "0x04",
        phooee = "0x05",
        noway = "0x03",
        kissmy = "0x02",
        booer = "0x01",
      },
      class_id = "0x896e75af",  -- Class ID of the automata. Often or always kept in
                                   the savegames while the automata is in use.
      models = {                -- Additional S3D models to use, if any.
        sprite_model("0x0001000"),
        sprite_model("0x0002000"),
        sprite_model("0x0003000")
      },
    }

### Attractor Block

The Attractor Block is used for drawing (attracting) nearby sprites. The below example shows an attractor that attracts and repels school kids. Attractor strengths range from -100 to 100, with negative values repelling and positive values attracting. There are three ways to define attractor strength, one of which is demonstrated in the example code, with the other two demonstrated in the comments of the code.

    attractor.schoolkids_attractor = 
    {
      strength = { 80, 0 },                  -- This example falls off to 0 at max radius.
        -- strength = 80,                    -- This example would be at constant
                                                strength 80 throughout the radius.
        -- strength = { -80, -80, -80, 20 }, -- And this example repels for 3/4 of the radius,
                                                then attracts at the outer edge.
      radius = 50,                           -- Influence radius, in meters.
      automata = { "child" },                -- Automata_groups this attractor affects.
      calendar = { monday, tuesday, wednesday, thursday, friday },
      time_of_day = {
        [7] = 0.0,      -- Start to ramp up at 7 AM...
        [8] = 1.0,      -- to max attraction strength at 8 AM,
        [8.5] = 0.3,    -- then taper off.
        [9.0] = 0.0,  
        [14.9] = 0.0,   -- Suddenly...
        [15.0] = -1.0,  -- ...go home at 3PM (negative values repel),
        [15.5] = 0.0    -- and a final ramp down value for the day.
      },
      behavior = {                         
          -- Behavior is always expressed as a table of tables, since there can be more than 1.
        { 
          radius = 15,                     -- When automata are within 10 meters...
          state = BehaviorState.DISAPPEAR, -- They should disappear as if going into the building.
        },
        {
          radius = 30,                     -- When automata are within 30 meters...
          state = BehaviorState.BEE_LINE,  -- They should break from paths and head straight towards the building.
        },
      },
    }

### Generator Block

This block is used for generating objects. The example below shows a generator that creates school kids.

    generator.schoolkids_generator = 
    {
      automata = { "child" },            -- Create children.
      occupancy_pct = 0.2,               -- Generate 20% of school's occupancy...
      rate = 2,                          -- ...two times...
      rate_scale = RateScale.PER_MINUTE, -- ...per game minute.
      radius = { 10, 50 },
        -- Generate at random distances between 10 and 50 meters away.
        -- If this generator is linked to a time_of_day clock, then negative values will cause the
        -- automata to be generated towards the inside of the range, and positive values will create
        -- them towards the outside of the range (so that they will mimic an attached attractor).

      -- Copy times from schoolkids_attractor, seen above:
      calendar = { monday, tuesday, wednesday, thursday, friday },
      time_of_day = {
        [7] = 0.0,      -- Start to ramp up at 7 AM...
        [8] = 1.0,      -- to max attraction strength at 8 AM,
        [8.5] = 0.3,    -- then taper off.
        [9.0] = 0.0,  
        [14.9] = 0.0,   -- Suddenly...
        [15.0] = -1.0,  -- ...go home at 3PM (negative values repel),
        [15.5] = 0.0    -- and a final ramp down value for the day.
      },
    }

### Occupant Block

This block contains occupant data. The example below shows how to create a "school" occupant group. Each occupant that belongs to this group will have a "schoolkids_attractor" and "schoolkids_generator" attached to it.

    occupant_group.school = 
    {
      group_id = "0x8a1ddfb4",
        -- This should be a GUID defined in ingred.ini's "occupant groups" value map.
        -- Alternatively, you could create an occupant group without giving it its
           own GUID or changing a property in the exemplars.  Since all school buildings
           have the "school coverage radius" property, you could un-comment the following line.
        -- Then, any time an occupant is created and it has that property, it will be made a
           part of the "school" occupant group and have a "schoolkids_attractor"
           and "schoolkids_generator" attached to it.

      -- property_check = { "0x691b42b3" },  -- "School Coverage Radius"

      controllers = {
       "schoolkids_attractor",
       "schoolkids_generator"
      },
    }

### End Block

    -- verify_all_templates()
      -- When un-commented this tells the script to verify its validity
         against the templates file. This clogs down the program, however.
    end
      -- This ending command is included where non-standard data
         such as functions or if statements are used.
