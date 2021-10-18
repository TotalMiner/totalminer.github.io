
# (Official) Console Documentation

## notify

Post a screen notification.

___

Add a notification to top left of screen.

notify -a -c -g -l -r [message]

-a  -- notification appears on the screen for admins.
-c  -- notification appears on the screen for all members of the current players clan.
-g  -- notification appears on the screen for all gamers (default).
-l  -- notification only appears on your screen (local).
-r  -- notification appears on the screen for all remote gamers, but not yours.
[message]  -- the notification text. Surround the message with double quotes if it contains spaces.

Example:
notify "hello everyone"
notify -g "hello everyone"
The notification appears on every gamers screen.

notify -a "meeting time"
The notification appears only on admin screens.

___

### [back](../commands)