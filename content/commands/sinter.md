{
  "title": "SINTER",
  "summary": "Intersect multiple sets",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N*M) worst case where N is the cardinality of the smallest set and M is the number of sets.",
  "since": "1.0.0",
  "return_summary": "@array-reply: list with members of the resulting set.",
  "syntax": "key ...",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns the members of the set resulting from the intersection of all the given
sets.

For example:

```
key1 = {a,b,c,d}
key2 = {c}
key3 = {a,c,e}
SINTER key1 key2 key3 = {c}
```

Keys that do not exist are considered to be empty sets.
With one of the keys being an empty set, the resulting set is also empty (since
set intersection with an empty set always results in an empty set).

@examples

```cli
SADD key1 "a"
SADD key1 "b"
SADD key1 "c"
SADD key2 "c"
SADD key2 "d"
SADD key2 "e"
SINTER key1 key2
```

