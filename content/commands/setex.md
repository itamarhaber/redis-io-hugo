{
  "title": "SETEX",
  "summary": "Set the value and expiration of a key",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "key seconds value",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Set `key` to hold the string `value` and set `key` to timeout after a given
number of seconds.
This command is equivalent to executing the following commands:

```
SET mykey value
EXPIRE mykey seconds
```

[SETEX](/commands/setex) is atomic, and can be reproduced by using the previous two commands
inside an [MULTI](/commands/multi) / [EXEC](/commands/exec) block.
It is provided as a faster alternative to the given sequence of operations,
because this operation is very common when Redis is used as a cache.

An error is returned when `seconds` is invalid.

@examples

```cli
SETEX mykey 10 "Hello"
TTL mykey
GET mykey
```

