{
  "title": "TYPE",
  "summary": "Determine the type stored at key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply: type of `key`, or `none` when `key` does not exist.",
  "syntax": "key",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Returns the string representation of the type of the value stored at `key`.
The different types that can be returned are: `string`, `list`, `set`, `zset`,
`hash` and `stream`.

@examples

```cli
SET key1 "value"
LPUSH key2 "value"
SADD key3 "value"
TYPE key1
TYPE key2
TYPE key3
```

