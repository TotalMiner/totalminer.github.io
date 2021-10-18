
# (Official) Console Documentation

## cmd

Execute cmd file.

___

Execute all the console commands in a cmd file.

cmd [name] [args]

[name] -- The name of the command file. This will be a *.cmd file residing in the maps save folder on disk. You can create these files using any text editor.
[args] -- Optional arguments that can be passed to the commands inside the command file.

Example:
cmd crates -- This will run all the console commands in the crates.cmd file found in the maps save folder.
crates -- This will also run all the console commands in the crates.cmd file found in the maps save folder.

Note: cmd is only necessary if the name of the .cmd file conflicts with an existing console command name. For crates, because there is no crates console command, you can just type crates without the preceding cmd, and the crates.cmd file will be executed.

Argument substitution is possible with cmd files, similar to MSDOS batch files. If the command in the cmd file uses %n (where n is a number starting from 1) as an argument, then the corresponding argument passed with the cmd command will be substituted for the %n argument in the cmd file.

Example:
If we have a cmd file named welcome.cmd with the following commands:
notify %1
notify %2

Then the following are examples of the output:

cmd welcome hello everyone
notify hello
notify everyone

cmd welcome hello john
notify hello
notify john

cmd welcome sup dawg
notify sup
notify dawg

___

### [back](../commands)