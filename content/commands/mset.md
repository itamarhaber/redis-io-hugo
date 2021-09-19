{
  "title": "MSET",
  "summary": "Set multiple keys to multiple values",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys to set.",
  "since": "1.0.1",
  "return_summary": "@simple-string-reply: always `OK` since `MSET` can't fail.",
  "syntax": "key value ...",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Sets the given keys to their respective values.
[MSET](/commands/mset) replaces existing values with new values, just as regular [SET](/commands/set).
See [MSETNX](/commands/msetnx) if you don't want to overwrite existing values.

[MSET](/commands/mset) is atomic, so all given keys are set at once.
It is not possible for clients to see that some of the keys were updated while
others are unchanged.

@examples

```cli
MSET key1 "Hello" key2 "World"
GET key1
GET key2
```

