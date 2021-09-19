{
  "title": "SDIFF",
  "summary": "Subtract multiple sets",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the total number of elements in all given sets.",
  "since": "1.0.0",
  "return_summary": "@array-reply: list with members of the resulting set.",
  "syntax": "key ...",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns the members of the set resulting from the difference between the first
set and all the successive sets.

For example:

```
key1 = {a,b,c,d}
key2 = {c}
key3 = {a,c,e}
SDIFF key1 key2 key3 = {b,d}
```

Keys that do not exist are considered to be empty sets.

@examples

```cli
SADD key1 "a"
SADD key1 "b"
SADD key1 "c"
SADD key2 "c"
SADD key2 "d"
SADD key2 "e"
SDIFF key1 key2
```

