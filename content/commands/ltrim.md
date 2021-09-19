{
  "title": "LTRIM",
  "summary": "Trim a list to the specified range",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of elements to be removed by the operation.",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "key start stop",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Trim an existing list so that it will contain only the specified range of
elements specified.
Both `start` and `stop` are zero-based indexes, where `0` is the first element
of the list (the head), `1` the next element and so on.

For example: `LTRIM foobar 0 2` will modify the list stored at `foobar` so that
only the first three elements of the list will remain.

`start` and `end` can also be negative numbers indicating offsets from the end
of the list, where `-1` is the last element of the list, `-2` the penultimate
element and so on.

Out of range indexes will not produce an error: if `start` is larger than the
end of the list, or `start > end`, the result will be an empty list (which
causes `key` to be removed).
If `end` is larger than the end of the list, Redis will treat it like the last
element of the list.

A common use of [LTRIM](/commands/ltrim) is together with [LPUSH](/commands/lpush) / [RPUSH](/commands/rpush).
For example:

```
LPUSH mylist someelement
LTRIM mylist 0 99
```

This pair of commands will push a new element on the list, while making sure
that the list will not grow larger than 100 elements.
This is very useful when using Redis to store logs for example.
It is important to note that when used in this way [LTRIM](/commands/ltrim) is an O(1) operation
because in the average case just one element is removed from the tail of the
list.

@examples

```cli
RPUSH mylist "one"
RPUSH mylist "two"
RPUSH mylist "three"
LTRIM mylist 1 -1
LRANGE mylist 0 -1
```
