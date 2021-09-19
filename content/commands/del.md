{
  "title": "DEL",
  "summary": "Delete a key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys that will be removed. When a key to remove holds a value other than a string, the individual complexity for this key is O(M) where M is the number of elements in the list, set, sorted set or hash. Removing a single key that holds a string value is O(1).",
  "since": "1.0.0",
  "return_summary": "@integer-reply: The number of keys that were removed.",
  "syntax": "key ...",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

Removes the specified keys.
A key is ignored if it does not exist.

@examples

```cli
SET key1 "Hello"
SET key2 "World"
DEL key1 key2 key3
```

