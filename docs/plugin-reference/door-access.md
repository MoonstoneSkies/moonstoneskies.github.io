---
layout: page
title: Door Access
parent: Plugin Reference
---

# Door Access
The door access plugin is used to configure NPC pathfinding through doors. If you're trying to configure which keys a player can use to unlock a door, you want to use the `Access` attribute on the door itself.

Door access settings are applied on each side of the door - there's no reason that the access settings have to match from both directions. However, keep in mind if an NPC is allowed to walk through a door in one direction, they should be able to get back inside that area either through the same door or by another route.

If a door has multiple restrictions placed on it, the NPC only needs to qualify for one of them. A door marked `BasicKeycard SecurityKeycard` will allow a bot holding only a `BasicKeycard` to pass through it

## Access Display
Basic access settings for a door are displayed on a part in front of it while the plugin is open. You can check at a glance how things are configured

![Image]({{"/images/plugins/DoorAccess.png" | relative_url}})

## Settings
When opening the Door Access plugin, you'll see a list of settings pop up on the right. The "active" settings can be applied to a door by clicking on that door (click on the door itself, not the settings display part for that door). You can also copy the active settings of a door by mousing over it and hitting `C`. To break down what each setting configures:

### Locked
Configures if the door is locked from this side. Only affects players - if an NPC is not restricted from walking through this door from this direction, they'll be able to unlock/walk through it

### Recovery
Recovery is a non-standard state for NPCs that have been lured out of their standard patrol area. NPCs in a recovery state can walk through any door marked with the recovery flag, regardless of any other settings. Use this to ensure they can always get back to areas they're supposed to be in and don't get permanently stuck somewhere else

### Ignore When Open/Unlocked/Broken
When this door is Open/Unlocked/Broken, all NPCs will be able to path through it, regardless of any other restrictions. The exception to this is the Never setting

### Never
No NPCs should ever be able to use this door, under any circumstances

### Combat
Restricts this door to combat NPCs. Combat NPCs are NPCs specifically spawned by a combat spawner component, and doesn't apply to guards who have been alerted and are now shooting at players

### Keycards, Badges, and Keys
Restricts this door to NPCs carrying specific items. You can also use custom items for this (see below)

## Custom Access Settings
You can also apply custom access settings to a door by manually modifying the `PathReq1` and `PathReq2` attributes. You can add any item to these to allow only NPCs with that item to cross. Copying active settings on a door with the plugin also copies these, although it won't be shown on the UI