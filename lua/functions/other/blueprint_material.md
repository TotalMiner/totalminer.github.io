
# (Official) LUA Scripting Documentation

## blueprint_material
#
### Define the material for a blueprint (crafting recipe) slot.
#
Spec:
```lua
blueprint_material(
	item_id,
	slot_id,
	slot_item_id,
	slot_qty,
	slot_durability)
```
#
## Parameters:
- `item_id:` The item being crafted
- `slot_id:` The slot number for this material (1 - 9)
- `slot_item_id:` The material item for this slot
- `slot_qty:` The qty needed of the slot item for a single craft
- `slot_durability:` The durability subtracted from the slot item on a single craft
#
### [back](../other)
