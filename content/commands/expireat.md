{
  "title": "EXPIREAT",
  "summary": "Set the expiration for a key as a UNIX timestamp",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.2.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the timeout was set.\n* `0` if the timeout was not set. e.g. key doesn't exist, or operation skipped due to the provided arguments.",
  "history": [
    [
      "7.0",
      "Added options: `NX`, `XX`, `GT` and `LT`."
    ]
  ],
  "syntax": "key timestamp [NX|XX|GT|LT]",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

[EXPIREAT](/commands/expireat) has the same effect and semantic as [EXPIRE](/commands/expire), but instead of
specifying the number of seconds representing the TTL (time to live), it takes
an absolute [Unix timestamp][hewowu] (seconds since January 1, 1970). A
timestamp in the past will delete the key immediately.

[hewowu]: http://en.wikipedia.org/wiki/Unix_time

Please for the specific semantics of the command refer to the documentation of
[EXPIRE](/commands/expire).

## Background

[EXPIREAT](/commands/expireat) was introduced in order to convert relative timeouts to absolute
timeouts for the AOF persistence mode.
Of course, it can be used directly to specify that a given key should expire at
a given time in the future.

## Options

The [EXPIREAT](/commands/expireat) command supports a set of options since Redis 7.0:

* `NX` -- Set expiry only when the key has no expiry
* `XX` -- Set expiry only when the key has an existing expiry
* `GT` -- Set expiry only when the new expiry is greater than current one
* `LT` -- Set expiry only when the new expiry is less than current one

A non-volatile key is treated as an infinite TTL for the purpose of `GT` and `LT`.
The `GT`, `LT` and `NX` options are mutually exclusive.

@examples

```cli
SET mykey "Hello"
EXISTS mykey
EXPIREAT mykey 1293840000
EXISTS mykey
```

