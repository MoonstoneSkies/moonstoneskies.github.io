---
layout: page
title: Meadow Map
parent: Plugin Reference
---

# Meadow Maps
Meadow maps are how your bots handle pathfinding through rooms. The meadow map plugin is you can view and modify the meadow map for a cell. Each cell in your mission should have it's own meadow map - the meadow map plugin will enforce only placing nodes in the currently opened cell.
## Controls
Control are printed in studio output whenever you open the plugin. Make sure you have studio output open when using any of the plugins. For reference:

* T - Opens a cell's meadow map. Your mouse cursor must be inside the cell to open it. If a cell doesn't have a meadow map, it automatically generates one based on links connected to that cell
* Double Tap C - Fully reset a rooms meadow map. Identical to hitting T when a room doesn't have a meadow map. This also regenerates the solid "Link" nodes for the cell, which doesn't happen when reopening an existing meadow map
* G - Add a node, and automatically link that node to others. Connections are generated based on line of sight
* H - Add a node, without automatically generating a connection between them
* R - Remove a node or connection. Note that connections are split into two parts, each designating a different direction of travel. By deleting only one, it's possible to have a connection that allows moving from point A to point B, but not from point B to point A
* LMB - Click on two nodes to create a connection between them

Changes to a cells meadow map save automatically when the plugin is closed.
### Auto Generated Nodes
When generating a meadow map for the first time, nodes will automatically be created for any doors or other links that enter the cell. These nodes will be fully opaque instead of transparent (like nodes created by G and H). These nodes aren't required and you can delete them if you want, but they mark the point the NPC will attempt to walk to when crossing that link. If you've added more doors to a cell since a meadow map was created, you can either fully regenerate it to get the new "link" nodes or just estimate their location and place them manually.

## Meadow Map Restrictions
### Moving Meadow Maps
Moving a cell does not move the meadow map inside of that cell - if you drag a cell or a mission to a new location after creating a meadow map for it, that meadow map will be offset and will likely break pathing when imported into a mission. This can also happen with template missions if they're moved on import - make sure workspace is clear before adding a template to avoid accidentally offsetting the meadow maps.

The sole exception to this is when using PartCollections - if a cell is moved by a part collection during mission initialization, it's meadow map will be updated alongside it to the new location.
### Node Connections
Every node in a meadow map should be connected to every other node - not necessarily directly, but there should always be a path through the node graph. An NPC on any node in a room will always assume that they can reach any other node in a room, and you may see strange NPC behavior if this is the case. If you find yourself needing a split node graph, consider splitting the area into multiple cells.
### Conditional Connections
Node connections can't be made conditional or altered dynamically at runtime. If you find yourself needing to conditionally gate NPC pathfinding through an area, split the area into multiple cells and place the conditions on the links
## Room Topography
The number and placement of your links should be based on the topography of the room. As a general rule, you want the nearest node to the NPC to be one they can walk to without running into any obstacles. some examples of meadow maps below:

### Open Room
![Image]({{"/images/plugins/MeadowMapExample1.png" | relative_url}})

In this case, we have a simple room with only a few props and none in the center. NPCs can reasonably be expected to reach the closest link node from anywhere in the room.

### Loop
![Image]({{"/images/plugins/MeadowMapExample2.png" | relative_url}})

Now that we've added obstacles in the center of the room, we need to provide nodes for pathing around them. Otherwise, NPCs would run into the center obstacle when they try to go to the lower part of the room. In this image you can see the difference between the opaque link nodes and the transparent nodes we added to facilitate pathing.

### Complex Room
![Image]({{"/images/plugins/MeadowMapExample3.png" | relative_url}})

Now that we have many more obstacles in the room, we've added nodes and connections around them. While it is possible to add more connections to this node set, especially around the bottom, we have enough here to provide reasonably direct pathing between any two nodes. 

## Default Pathfinding
If no meadow map data is attached to a cell, InfiltrationEngine will fall back to using the default pathfinding service built into the roblox engine, which is frequently inaccurate and handles prop collision poorly. The meadow map definition is also required for certain internal functions that pick random pathable points in a cell, like the NPC "search" function when they hear a suspicious noise
