# (Official) Behavior Tree Documentation

## IsHealth

Check the health of the target actor.

___
## Parameters

- `MaxOrCurrent`: Check the max or current health. If checking for percentage this must be set to Current.
- `CompareType`: The operation preformed for the comparison.
- `CompareTarget`: Sets if the comparison is applied to the NPC or the NPC's target.
- `Value`: The value to compare to.
- `Continue`: When set true the node will always succeed.
- `IsEnabled`: When set false the node will always fail.
- `Comment`: User comments.
