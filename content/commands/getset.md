{
  "title": "GETSET",
  "summary": "Set the string value of a key and return its old value",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@bulk-string-reply: the old value stored at `key`, or `nil` when `key` did not exist.",
  "deprecated": true,
  "syntax": "key value",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Atomically sets `key` to `value` and returns the old value stored at `key`.
Returns an error when `key` exists but does not hold a string value.  Any 
previous time to live associated with the key is discarded on successful 
[SET](/commands/set) operation.

## Design pattern

[GETSET](/commands/getset) can be used together with [INCR](/commands/incr) for counting with atomic reset.
For example: a process may call [INCR](/commands/incr) against the key `mycounter` every time
some event occurs, but from time to time we need to get the value of the counter
and reset it to zero atomically.
This can be done using `GETSET mycounter "0"`:

```cli
INCR mycounter
GETSET mycounter "0"
GET mycounter
```

As per Redis 6.2, GETSET is considered deprecated. Please prefer [SET](/commands/set) with [GET](/commands/get) parameter in new code.

@examples

```cli
SET mykey "Hello"
GETSET mykey "World"
GET mykey
```

