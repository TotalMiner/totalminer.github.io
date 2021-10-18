
# (Official) Console Documentation

## script

Execute a script.

___

Execute an existing script or single script command.

script -c -s [command|script]

-c  -- Run a single script command.
-s  -- Run a script (default switch, can be omitted).
[command] -- A single command to run.
[script]  -- A full script name to run, including folders. 

Examples:
script Events\PlayerJoined
script -s Events\PlayerJoined
Runs the script called Events\PlayerJoined.

script -c notify [hello [gamertag]]
Runs the single script command: notify [hello [gamertag]]

___

### [back](../commands)