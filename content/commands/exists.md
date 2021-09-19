{
  "title": "EXISTS",
  "summary": "Determine if a key exists",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys to check.",
  "since": "1.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the key exists.\n* `0` if the key does not exist.\n\nSince Redis 3.0.3 the command accepts a variable number of keys and the return value is generalized:\n\n* The number of keys existing among the ones specified as arguments. Keys mentioned multiple times and existing are counted multiple times.",
  "syntax": "key ...",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Returns if `key` exists.

Since Redis 3.0.3 it is possible to specify multiple keys instead of a single one. In such a case, it returns the total number of keys existing. Note that returning 1 or 0 for a single key is just a special case of the variadic usage, so the command is completely backward compatible.

The user should be aware that if the same existing key is mentioned in the arguments multiple times, it will be counted multiple times. So if `somekey` exists, `EXISTS somekey somekey` will return 2.

@examples

```cli
SET key1 "Hello"
EXISTS key1
EXISTS nosuchkey
SET key2 "World"
EXISTS key1 key2 nosuchkey
```

