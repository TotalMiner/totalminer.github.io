# (Official) Behavior Tree Documentation

## HasHistory

Compare a history value of the target actor or system.

___
## Parameters

- `HistoryName`: The history key to be compared against.
- `HistoryType`: The type of history. Can be Actor, Clan, or System.
- `CompareType`: The operation preformed for the comparison.
- `CompareTarget`: Sets if the comparison is applied to the NPC or the NPC's target.
- `Value`: The value to compare to.
- `Continue`: When set true the node will always succeed.
- `IsEnabled`: When set false the node will always fail.
- `Comment`: User comments.
