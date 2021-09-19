{
  "title": "MGET",
  "summary": "Get the values of all the given keys",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys to retrieve.",
  "since": "1.0.0",
  "return_summary": "@array-reply: list of values at the specified keys.",
  "syntax": "key ...",
  "acl_categories": [
    "string",
    "slow"
  ]
}

Returns the values of all specified keys.
For every key that does not hold a string value or does not exist, the special
value `nil` is returned.
Because of this, the operation never fails.

@examples

```cli
SET key1 "Hello"
SET key2 "World"
MGET key1 key2 nonexisting
```

