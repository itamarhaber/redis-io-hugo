Returns @array-reply of keys from a full Redis command.

[COMMAND GETKEYS](/commands/command-getkeys) is a helper command to let you find the keys
from a full Redis command.

[COMMAND](/commands/command) shows some commands as having movablekeys meaning
the entire command must be parsed to discover storage or retrieval
keys.  You can use [COMMAND GETKEYS](/commands/command-getkeys) to discover key positions
directly from how Redis parses the commands.


@examples

```cli
COMMAND GETKEYS MSET a b c d e f
COMMAND GETKEYS EVAL "not consulted" 3 key1 key2 key3 arg1 arg2 arg3 argN
COMMAND GETKEYS SORT mylist ALPHA STORE outlist
```

