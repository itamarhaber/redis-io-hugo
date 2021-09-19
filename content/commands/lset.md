{
  "title": "LSET",
  "summary": "Set the value of an element in a list by its index",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the length of the list. Setting either the first or the last element of the list is O(1).",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "key index element",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Sets the list element at `index` to `element`.
For more information on the `index` argument, see [LINDEX](/commands/lindex).

An error is returned for out of range indexes.

@examples

```cli
RPUSH mylist "one"
RPUSH mylist "two"
RPUSH mylist "three"
LSET mylist 0 "four"
LSET mylist -2 "five"
LRANGE mylist 0 -1
```

