---
title: "LUAMission"
description: ""
published: false
date: '2019-08-04T05:40:51Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-10T02:13:30Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**Mission LUA Files** control the game's [U-Drive-It](/u-drive-it) missions almost in their entirety. They contain all the data related to the actual mission but not the data for each vehicle. There is one [LUA](/lua) file for each type of vehicle with all the missions for that vehicle contained in it. The Mission LUAs are pretty standard scripts with the occasional bit of system Lua programming. This file should now contain all used options and functions for missions. It appears that new mission files cannot be created, however individual missions for any mission file can be added to that file.

The first half of this file down to the "Other Options" area was written by [Buggi](/people/buggi).

## Example Specification

The mission files usually start out looking like this:

    ----------------------------------
    --Attack Helicopter Missions -- Take Out Dr. Vu's "Secret" Lair - good
    -----------------------------------

Usually saying what vehicle is used, what the name is, and whether it's good or evil. So this file ([TGI](/tgi) CA63E2A3 - 4A5E8EF6 - FFA4B9DA) contains all of the attack helicopter missions.

Go find that file and check it out. This next part goes through the first mission line-by-line and tries to describe what things mean. This will get a little long.

    s = create_advice_citysituation('2c14348d')
       -- This line gives the mission a unique GUID. These ID's have to be unique.
     
    s.title = "text@6C154452"
       -- This line simply tells the program where the localizable string is for the title.
       -- To change, simply enclose the new string in double braces... like so s.title = [[Save the Monkeys!]]
     
    s.message = [[text@06C15438]]
       -- This also tells the game where to find the text,
          anytime it sees text@GUID that's where it looks in the simcitylocale.dat file.
     
    s.priority=tuning_constants.ADVICE_PRIORITY_LOW 
       -- This can be 1-100 or VERY_LOW, LOW, MED_LOW, MED_MED_LOW,
          MEDIUM, MED_HIGH, HIGH, URGENT (all with ADVICE_PRIORITY as the prefix).

    s.automata_list = automata_groups.military_helicopter
       -- This tells what vehicle the mission actually uses. There are about 130 of them,
          obviously only a few are actually valid to this system.
     
    s.target_sequence {} -- optional!
       -- This defines where you're going to go in this mission. It's a table so it can be more than one.
          About 120 exist for use. Not sure yet how many are valid.
       -- An example would be (for like a bus mission):
               s.target_sequence {
               building_groups.STADIUM,
               building_groups.RESIDENTIAL
               }

Next is information about the targets and conditions of the mission:

    s.condition = sit_conditions.TARGET_DESTROYED
       -- Obviously this one is what needs to happen in order for it to be a success.
          This is from that attack chopper mission so you need to destroy whatever it
          picks at the target (in this case an industrial building). Or in the example above
          the stadium and a residential building.
       -- The options are REACH_TARGET, ESCAPE_CITY, TARGET_DESTROYED, SCRIPTED, CELL_COVERAGE
     
    s.create_target = false
       -- This line tells the mission engine that if the target does not exist,
          to create one. Usually false for buildings, true for automata.
     
    s.success_distance = sit_constants.SUCCESS_DISTANCE_SHORT
       -- How close your vehicle has to be to the target to be called a "success".
       -- Options are _SHORT, _BOAT, and _MEDIUM
     
    s.success_timeout = sit_constants.SUCCESS_TIMEOUT_SHORT
       -- How much time player has to be within the object (used in combo with DISTANCE).
       -- Options are _SHORT, _BOAT, _AIR
     
    s.min_target_distance = sit_constants.MIN_TARGET_DISTANCE_SHORT
       -- Targets chosen must be a minimum of this close to the vehicle.
       -- Options are _SHORT, _BOAT, _LONG 
     
    s.max_target_distance = sit_constants.MAX_TARGET_DISTANCE_SHORT
       -- Furthest away a target can be. 0 is no limit, the above equals 0 so
          this mission has no limit on how far away the target is.

The following are optional parts of the mission:

    s.time_limit = sit_constants.TIME_LIMIT_SHORT
       -- Time limit to put on this mission...In real time, 0 = infinite.
     
    s.success_text = [[text@EC154554]]
    s.reward_unlocked_text = [[text@EC193CF4]]
       -- Both similar to above text. 
     
    s.reward_guid  = hex2dec('032F0000') --advance research center
       -- Unlocks the Advanced Research Center if successful. 0x032F is the GUID of the reward.  Oh the possibilities...
     
    s.failure_text = [[text@2C15455D]]
       -- Same as other text...
     
    s.frequency = sit_constants.FREQUENCY_SHORT
       -- Number in days. This is 365.  You also have _FIRST which is just 1 and _MYSIM_SHORT which is 10.
     
    s.trigger=""
       -- VITAL - This tells the game what conditions have to be met before this mission is available.
          If the syntax is wrong here, or the condition doesn't exist internally, the mission
          won't be used. More detail on this in a later post.
     
    s.image = sit_constants.SITUATION_IMAGE_SAFETY
       -- Image of person that pops up when this mission is clicked on.
       -- Options are _UTILITIES, _HEALTH_EDUCATION, _CITY_PLANNING, _TRANSPORTATION, _ENVIRONMENT,
          _FINANCES, _SAFTY, _DR_VU, _DEFAULT, _CARJACK, _BANK_ROBBERY, _POLICE_HELICOPTER,
          _POLICE_ARREST, _SUCCESSFUL_ROBBERY
     
    s.success_image = sit_constants.SITUATION_Reward_Advanced_Research_Center
       -- Image to use in the success box. Like in my monkey shot I used:
               sit_constants.SITUATION_Reward_Bureau_Of_Bureaucracy
       -- It doesn't GIVE them the building, just uses that icon. They're about 60 of them...
     
    s.failure_image = sit_constants.SITUATION_IMAGE_SAFETY 
       -- Uses the same values as s.image only if you fail the mission.
     
    s.mood = advice_moods.NEUTRAL
       -- Options are ALARM, BAD_JOB, NEUTRAL, GREAT_JOB, FLUFF
     
    s.failure_mood = advice_moods.BAD_JOB
       -- Same as above.
     
    s.evil_twin = hex2dec('6c143492')
       -- Sets the 'evil twin', the GUID used is the same set in the very first line.
          If it IS the evil mission, it points to the good one, or just general alternates.
          So you could daisy chain 20 missions on one vehicle if you wanted.
          Basically a linked list of missions. (For the programmers out there)
     
    s.success_aura_radius  = sit_constants.HAR_GOOD_SUCCESS_AURA_RADIUS
       -- Sets the values to be used in the aftermath of the mission.
     
    Same with the others:

    s.success_aura_magnitude = sit_constants.HAR_GOOD_SUCCESS_AURA_MAG
    s.failure_aura_radius = sit_constants.HAR_GOOD_FAILURE_AURA_RADIUS
    s.failure_aura_magnitude = sit_constants.HAR_GOOD_FAILURE_AURA_MAG
     
    s.success_effect = sit_constants.SUCCESS_EFFECTMAYRAT
       -- What does the screen do when successful. This is the neat glowing balls effect.
       -- Options are _EFFECTMAYRAT, _EFFECTMONEY, _EFFECTMAYRAT_MONEY
     
    s.failure_effect = sit_constants.FAILURE_EFFECT
       -- Same as above, only if you fail.
       -- Options are _FAILURE_EFFECT, _FAILURE_EFFECTMONEY, _FAILURE_EFFECTDARKMONEY

Remember both GOOD and EVIL are used for radius and magnitude above.

## Other Options

These are the other options that missions can use, including the function scripting contained in each mission.

    s.progress_text = { 
         [[text@6c3e39dd]],
         [[text@6c3e39dd]],
         [[text@2c27da59]]
         }
       -- A function like this uses LTEXT strings that are called after each target
          in the target sequence is reached, but not counting the success text.
          An example would be reaching a school, at which point the text would
          tell you to go to the dump to throw out the kids in the garbage :-)

    s.reward_progress_text = [[text@4C193E67]]
       -- LTEXT GUID to be displayed if this mission does not fully unlock a reward.

    s.evade_list = { automata_groups.getaway_van }
       -- The automata groups for the vehicles you are trying to evade. Ones seen used
          are the getaway_van, patrol_car, and police_helicopter. Any other automata group name
          should be sufficient, however. Automata groups are separated by commas.

    s.evade_distance = sit_constants.EVADE_DISTANCE_SHORT
       -- The distance that you have to be from the pursuing vehicle in order for you to be
          considered evading it. You should be able to use main variables for the end part,
          for example, _SHORT,_MEDIUM,_LONG. This hasn't been confirmed, but would be logical
          for all the variables to be this way.

    s.evade_timeout = sit_constants.EVADE_TIMEOUT_SHORT
       -- How long you must be outside evade distance to be considered to have evaded the target completely.
          Again, short, medium, and long should work for this. Used in conjunction with evade distance.
       -- This may also be a simple variable such as "s.evade_timeout = 10" for 10 seconds.

    s.coverage_cells_min   = 20
       -- Minimum number of mission cells (red squares that must be passed through) for this mission.

    s.coverage_cells_max   = 20
       -- Maximum number of mission cells (red squares that must be passed through) for this mission.
          Used with min coverage.

    s.coverage_cells = { {0,-2}, {1,-3}, {2,-4},{3,-4}, {4,-3}, {5,-2}, {5,-1}, {4,0}, {3,1}, {2,2}, {1,3}, {0,4},
                         {-1,3}, {-2,2}, {-3,1}, {-4,0}, {-5,-1}, {-5,-2}, {-4,-3}, {-3,-4}, {-2,-4}, {-1,-3}, {0,-1} }
       -- Cell pattern to be declared as target based off of main target point found by system.
          These are x,z points based off the home target point.

    s.coverage_rect = { 30, 30, 35, 35, }
       -- Rectangle of cells to be declared as target based off of the home target like cells are. x1,z1,x2,z2

    s.coverage_network = network_types.OVER_GROUND
       -- Never actually seen this truly used, however the cells must be on a network in this case,
          and OVER_GROUND networks are the clause, i.e. roads, streets, etc. This is the only used value seen.

    s.coverage_success_count = 15
       -- If all cells do not need to be covered for success, the amount that must be covered is this value.

    s.success_money = sit_constants.MED_EVIL_SUCCESS_MONEY
    s.failure_money = sit_constants.MED_EVIL_FAILURE_MONEY
       -- Success money and Failure money awarded. The Values can be either MED or HAR,
          and EVIL or GOOD, depending on the mission.

    s.coverage_type = sit_coverage_type.ZONE
       -- The type of cell coverage needed for the mission.
       -- Types known are ZONE, LOT, UNZONED_LAND, or CELLS

    s.coverage_zone = zone_tool_types.RESIDENTIAL_LD
       -- If the coverage type is zone, the type of zone that the mission needs coverage for.
       -- Values can be RESIDENTIAL_,COMMERCIAL_, INDUSTRIAL_, with the subvalues being
          LD,MD,HD,RES, or HEAVY where needed. Dunno about Industrial Manufacturing.

    s.coverage_lot = building_groups.CEMETARY
       -- If the coverage type is lot, the type of lot that the mission needs coverage for.
          Only seen CEMETARY, though other building types should be possible.

    s.use_lot_boundary = true
       -- Use the lot boundary as a target reached marker?

    s.mysim_mission = true
       -- Is the mission for MySims only?

    s.active_radius = 4
       -- Active radius to search for a target point within.

    s.pursuit_mission = true
       -- Does this mission have a criminal pursuit in it? (for police)

    s.event = game_events.DISASTER_STARTED_FIRE
       -- This mission is based off of an event. This event is a fire.
          It can't be player created as those have a _PLAYER_ clause in them after the _STARTED_,
          therefore create this event where needed.
       -- This can of course be cancelled with a "create target = false" option.

    s.service_mission = true
       -- Is this a service mission? Examples of service missions include firefighting,
          delivering things, fishing, skywriting, etc. Its unsure whether the game actually
          takes notice of this, however use it where applicable for best results.

## System Functions

System functions come after the main options and the trigger.

    function s:init()
       local target
       target = sc4game.sitmgr.get_current_target()
      (((insert clause here)))
    end
       -- This function usually starts off the function area where used. What it is used for
          is determining things that happen at the very start of the mission. It will always
          contain the "local target", "target =", and "end" lines. Examples of valid clauses for use would be:
              if (target ~= nil) then
          target.push_state(automata_states.IDLE)
          end
       -- This clause is basically an if statement that if true will make sure the state of the target is idle.

       sc4game.automata.attach_controller_group("striking_education", target);
       -- This clause attaches an animation group called striking_education (wonder what that is)
          to the target, which is a school.
       -- You can use other clauses however these are ones I've seen Maxis use.
       -- Target may be substituted for Auto if you're wanting to do something with your vehicle.

    function s:get_time_limit(distToTarget, maxSpeed)
       local result
       (((use clause)))
       return result
    end
       -- This function determines the time limit of the mission and is used much more often than
          the above option for time limits. The clause can basically be any combination of system
          Lua functions that can or cannot use the distance to target, or vehicle max speed,
          which are fed to the function by default.
       -- An example good clause would be:
                 result = 15 + (distToTarget / maxSpeed) * 5
                    -- limit to min/max
                 if (result < 15) then
             result = 15
                    --elseif (result > 600) then      (note: 600 seconds == ten minutes)
                --result = 600
                 end
              -- This says to divide the distance to target, by the max speed, multiply by 5 and add 15
                 for the timeout value. if its less than 15 seconds, then make it 15 seconds.
                 If you want a set time for a mission, then just put in "result = ((your time))" for the entire clause.

    function s:on_success()
       local target
       target = sc4game.sitmgr.get_current_target()
    (((thing to do)))
    end
       -- On mission success, do this function. The thing to do can once again by anything you want. A good example would be:
       sc4game.automata.detach_controller_group("striking_education", target);
       -- Where the game takes away the animations for the strikers from the school when you beat that mission.
       -- Target may be substituted for Auto if you're wanting to do something with your vehicle.

    function s:on_failure()
       -- play bust animation on the getaway van
       local auto
       auto = sc4game.sitmgr.get_active_auto()
       (((thing to do)))
    end
       -- Basically the same as on success, this function demonstrates using auto to do
          something to your vehicle, instead of to the target. A good result in this case would be:
       auto.automata_attach_anim(automata.MODEL_TYPE_ID, automata.MODEL_GROUP_ID, hex2dec('0x117B0000'))
       -- Where the game takes an animation and attaches it to your vehicle. In this case the getaway van.
          the HEX ID is the instance id for the animation.

## Trigger Function

The Trigger function as pointed out at the start of this file.

    s.trigger="game.g_num_elem_schools > 0 and game.g_city_r_population > 50 and (sc4game.sitmgr.get_success_count('8c151efd') > 0)"
    -- adv_game_data.lua
       -- This is an example of a really simple trigger for the mission.
          They're basically giant if statements that use all your cities variables
          to determine if it's a right time to offer the mission to you.

In this case, it says the number of elementary schools and the residential population must both be above 0. In addition, the proper number of successes for this mission type must have been completed.

Usable main values:

    game.g_num_elem_schools
    game.g_city_r_population
    game.g_city_c_population
    game.g_city_i_population
    game.g_monorail_tile_count
    game.g_seaport_count
    game.g_city_cs1_population
    mysim.home_building ~= 0
       -- Any other number of variables may be substituted in here and used in and/or statements.

    sc4game.automata.get_source_building_count(building_groups.Monorail)
       -- Get number of automata source buildings for this building type. 

    game.reward_instance_count(special_buildings.ArmyBase)
       -- Get number of this type of reward for the city.

    (sc4game.sitmgr.get_success_count('missiontype') > 0)
       --Get the number of successes for this type of mission where the missiontype
         is the hexid for this group of missions. Types of missions are below.

### Types of Missions

- cc1730cf - Water Missions
- 8c151efd - Ground Missions
- ac1726c8 - Air Missions
- 2c1725c1 - Train Missions
- 4c4694f6 - Monorail Missions
