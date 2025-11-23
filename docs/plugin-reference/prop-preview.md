---
layout: page
title: Prop Preview
parent: Plugin Reference
---
# Prop Preview
Prop preview is used to visually display props in your mission while you're working on them in studio. Previewed props will automatically update their location when their base part is moved, and will update their appearance when their Color/Material attributes are updated. The prop preview toggle stays applied even when the plugin isn't selected, allowing you to use it with other tools and while building

Prop Preview also has a search function - you can search and insert props by name into your mission. 
## Functional Props
While you can use this plugin to insert functional props, it's recommended to find a version of a functional prop in a sample mission and copy that instead. Functional props often have several attributes that need to be set and it's often easier to modify one that's already been set up.
## Scalable Props
Specific scalable props are scripted to work with prop preview. This means you can resize these props and see the model update live in studio. These props are:
* ClimbablePipe
* DecorativePipe
* DecorativeVent
* GarageDoor
* Ladder
* ScalablePlanter
* ScalableWallPlanter
* ThinBush
* Window

## Limitations
Aside from the props listed above, no scripted changes to props will be applied to their preview. As a few examples:
* Double Doors will render as a single door in preview mode
* Cameras will not update to the actual rotation they will use in game
* Landscape photo variants won't render the actual photo based on their

Many props that don't have a model are not included in prop preview and can't be inserted via the plugin. Copy them from existing missions.