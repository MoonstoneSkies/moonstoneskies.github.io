---
layout: page
title: Section Visibility
parent: Plugin Reference
---

# Section Visibility
Section visibility is used to hide less frequently edited mission components out of the way when they're not needed. The components that it can hide are:
* Barrier
* Cell
* Nodes
* LoudSpawns

Even when these parts are invisible, they can frequently get in the way when trying to move or edit other things in the level. This plugin can be useful to get these sections collision out of the way for other edits.

Other plugins that depend on or edit hidden sections will temporarily unhide them while they're active. This includes the Exporter plugin

Hidden content is stashed in ReplicatedStorage, and uses a Stash ObjectValue in the mission data to point back to the hidden content. If that ObjectValue is destroyed, you need to restore the hidden content manually. Do not add anything to a folder that's "hidden" in DebugMission, or the additions will be lost when the folder is unhidden.