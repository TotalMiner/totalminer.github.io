
# (Official) Console Documentation

## inv

Manipulate the current players inventory.

___

Manipulate the current players inventory.

inv -a -e -r -ra [item] [qty]

-a   -- Add the item to inventory. If [qty] is omitted, the items default stack size will be added. If no other -args are used, -a is assumed.
-e   -- Equip the item. Optional. Can be used in conjunction with -a.
-r   -- Remove the item from inventory. If [qty] is omitted, all stacks of the item will be removed.
-ra  -- Remove all items.
[item]  -- The item to add/remove/equip/list.
[qty]  -- The number of units. 

Examples:
inv grass  -- add a stack of grass (-a assumed).
inv -a -e dirt 50  -- add 50 dirt and equip.
inv -e dirt  -- equip dirt if in inventory.
inv -r dirt  -- remove all stacks of dirt.
inv -r dirt 50  -- remove 50 dirt.
inv -ra  -- remove all items.

___

### [back](../commands)