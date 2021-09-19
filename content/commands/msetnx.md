{
  "title": "MSETNX",
  "summary": "Set multiple keys to multiple values, only if none of the keys exist",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys to set.",
  "since": "1.0.1",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the all the keys were set.\n* `0` if no key was set (at least one key already existed).",
  "syntax": "key value ...",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Sets the given keys to their respective values.
[MSETNX](/commands/msetnx) will not perform any operation at all even if just a single key already
exists.

Because of this semantic [MSETNX](/commands/msetnx) can be used in order to set different keys
representing different fields of an unique logic object in a way that ensures
that either all the fields or none at all are set.

[MSETNX](/commands/msetnx) is atomic, so all given keys are set at once.
It is not possible for clients to see that some of the keys were updated while
others are unchanged.

@examples

```cli
MSETNX key1 "Hello" key2 "there"
MSETNX key2 "new" key3 "world"
MGET key1 key2 key3
```

