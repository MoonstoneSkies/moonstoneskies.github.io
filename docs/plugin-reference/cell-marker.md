---
layout: page
title: Cell Marker
parent: Plugin Reference
---

# Cell Marker
Cell marker is used to help layout cells for your mission. While equipped, it will show you a black box that it estimates to be the size of the room your cursor is in. Click to make that room a cell in your mission. If the cursor is inside of another cell, clicking will create a new roof part in that cell and resize the floor part of that cell to encompass both of them.

Newly created cells will have the Default name

## Cell Rules
All areas inside of your mission should be within a cell. A cell is a model made up of one or more `Roof` parts and one or more `Floor` parts - any area under at least one roof and over at least one floor is considered part of a cell. Many props won't function if they're not inside of a cell, and players can activate triggers unless they're inside of a cell as well. See the Cells page for more info

## Additional Controls
As with other plugins, these controls are printed to output when you equip the plugin
* T - Reoptimize cell floors. For any cell that only has one floor part, that floor will be resized to cover any space under any of the roof parts of that cell. Note that due to how the engine does cell checks, it's more efficient for cells to only have one floor part
* G - Show all cells. Makes every cell visible
* H - Hide all cells. Makes every cell invisible, but collision will still be there
* J - Hide named cells. Hide any cell not named "Default"
* K - Recolor cells. Makes all cells with the same name have a matching random color. Can be used to easily see divisions between zones
* L - Show manually placed cell links. These go in a Links folder inside the Cells folder