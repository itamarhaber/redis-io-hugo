{
  "title": "BRPOP",
  "summary": "Remove and get the last element in a list, or block until one is available",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of provided keys.",
  "since": "2.0.0",
  "return_summary": "@array-reply: specifically:\n\n* A `nil` multi-bulk when no element could be popped and the timeout expired.\n* A two-element multi-bulk with the first element being the name of the key\n  where an element was popped and the second element being the value of the\n  popped element.",
  "history": [
    [
      "6.0",
      "`timeout` is interpreted as a double instead of an integer."
    ]
  ],
  "syntax": "key ... timeout",
  "acl_categories": [
    "list",
    "blocking",
    "write",
    "slow"
  ]
}

[BRPOP](/commands/brpop) is a blocking list pop primitive.
It is the blocking version of [RPOP](/commands/rpop) because it blocks the connection when there
are no elements to pop from any of the given lists.
An element is popped from the tail of the first list that is non-empty, with the
given keys being checked in the order that they are given.

See the [BLPOP documentation][cb] for the exact semantics, since [BRPOP](/commands/brpop) is
identical to [BLPOP](/commands/blpop) with the only difference being that it pops elements from
the tail of a list instead of popping from the head.

[cb]: /commands/blpop

@examples

```
redis> DEL list1 list2
(integer) 0
redis> RPUSH list1 a b c
(integer) 3
redis> BRPOP list1 list2 0
1) "list1"
2) "c"
```

