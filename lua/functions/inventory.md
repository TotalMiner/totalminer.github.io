
# (Official) LUA Scripting Documentation

## Pages

- [Home](../../index)
- [Data Types](../data-types)
- [Functions](../functions)

## Functions to manipulate inventory

### [add_inventory](inventory/add_inventory)*

> Add or subtract a quantity of an item to/from the context actors inventory.

### [add_block_inventory](inventory/add_block_inventory)*

> Add or subtract a quantity of an item to/from a blocks inventory.

### [add_region_inventory](inventory/add_region_inventory)*

> Add or subtract a quantity of an item to/from all block inventories in a cubic region.

### [can_equip](inventory/can_equip)*

> Query whether or not the context actor can equip an item.

### [clear_inventory](inventory/clear_inventory)*

> Clear (remove) an item from the context actors inventory.

### [clear_block_inventory](inventory/clear_block_inventory)*

> Clear (remove) an item from a blocks inventory.

### [clear_region_inventory](inventory/clear_region_inventory)*

> Clear (remove) an item from all blocks inventories in a cubic region.

### [copy_inventory](inventory/copy_inventory)*

> Copy a block's inventory to another block.

### [copy_inventory_region](inventory/copy_inventory_region)*

> Copy all block inventories in a cubic region to another region.

### [equip](inventory/equip)*

> Cause the context actor to equip an item.

### [get_block_inventory](inventory/get_block_inventory)*

> Get the total count of an item in a block's inventory.

### [get_inventory](inventory/get_inventory)*

> Get the total count of an item in the context actors inventory.

### [move_inventory](inventory/move_inventory)*

> Move (transfer) a block inventory to another block.

### [move_inventory_from](inventory/move_inventory_from)*

> Move (transfer) a blocks inventory to the context actors inventory.

### [move_inventory_to](inventory/move_inventory_to)*

> Move (transfer) the context actors inventory to a block's inventory.

### [move_inventory_region](inventory/move_inventory_region)*

> Move (transfer) all block inventories in a cubic region to another region.

### [unequip](inventory/unequip)*

> Unequip an item.
