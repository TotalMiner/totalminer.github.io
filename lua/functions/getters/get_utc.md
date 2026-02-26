
# (Official) LUA Scripting Documentation

## get_utc

Returns the current UTC time.

___

Spec:

```lua
get_utc()
```

## Returns

- `long`: day. The current day in UTC.
- `long`: month. The current month in UTC.
- `long`: year. The current year in UTC.
- `long`: hour. The current hour in UTC.
- `long`: minute. The current minute in UTC.
- `long`: second. The current second in UTC.
- `long`: unix. The current UNIX timestamp (in seconds) in UTC.
- `long`: dayofyear. The current day of the year in UTC.
- `long`: weekday. The current day of the week (Sunday = 0, Saturday = 6) in UTC.

___

## Examples

```lua
get_utc().day
```

If the current utc date is 5/18/2026 this will return 18.

___

```lua
get_utc().dayofweek
```

If the current utc day is Monday this will return 1.

___

```lua
get_utc().unix
```

If the current utc date is 5/18/2002 (M/DD/YYYY) at 12:00pm this will return 1779105600. The UNIX timestamp is in seconds.

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
