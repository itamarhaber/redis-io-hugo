{
  "title": "SINTERCARD",
  "summary": "Intersect multiple sets and return the cardinality of the result",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N*M) worst case where N is the cardinality of the smallest set and M is the number of sets.",
  "since": "7.0.0",
  "return_summary": "@integer-reply: the number of elements in the resulting intersection.",
  "syntax": "key ...",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns the cardinality of the set which would result from the intersection of all the given sets.

Keys that do not exist are considered to be empty sets.
With one of the keys being an empty set, the resulting set is also empty (since set intersection with an empty set always results in an empty set).

@examples

```cli
SADD key1 "a"
SADD key1 "b"
SADD key1 "c"
SADD key2 "c"
SADD key2 "d"
SADD key2 "e"
SINTER key1 key2
SINTERCARD key1 key2
```

