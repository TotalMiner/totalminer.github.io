
# (Official) LUA Scripting Documentation

## add_inventory
#
### Add or subtract a quantity of an item to/from the context actors inventory.
#
Spec:
```lua
add_inventory(
	item_id,
	qty)
```
#
## Parameters:
- `item_id:` 
- `qty:` The quantity to add. If ommitted, 1 item will be added. Use a negative number to remove items from inventory
#  

### [back](../inventory)
