[BLMPOP](/commands/blmpop) is the blocking variant of [LMPOP](/commands/lmpop).

When any of the lists contains elements, this command behaves exactly like [LMPOP](/commands/lmpop).
When used inside a [MULTI](/commands/multi)/[EXEC](/commands/exec) block, this command behaves exactly like [LMPOP](/commands/lmpop).
When all lists are empty, Redis will block the connection until another client pushes to it or until the `timeout` (a double value specifying the maximum number of seconds to block) elapses.
A `timeout` of zero can be used to block indefinitely.

See [LMPOP](/commands/lmpop) for more information.

@examples

```cli
DEL mylist mylist2
LPUSH mylist "one" "two" "three" "four" "five"
BLMPOP 1 1 mylist LEFT COUNT 2
LRANGE mylist 0 -1
LPUSH mylist2 "a" "b" "c" "d" "e"
BLMPOP 1 2 mylist mylist2 LEFT COUNT 3
LRANGE mylist 0 -1
BLMPOP 1 2 mylist mylist2 RIGHT COUNT 10
LRANGE mylist2 0 -1
EXISTS mylist mylist2
```

