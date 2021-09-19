{
  "title": "BLMPOP",
  "summary": "Pop elements from a list, or block until one is available",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+M) where N is the number of provided keys and M is the number of elements returned.",
  "since": "7.0.0",
  "return_summary": "@array-reply: specifically:\n\n* A `nil` when no element could be popped, and timeout is reached.\n* A two-element array with the first element being the name of the key from which elements were popped, and the second element is an array of elements.",
  "syntax": "timeout numkeys [key ...] LEFT|RIGHT [COUNT count]"
}

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

