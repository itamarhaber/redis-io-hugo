{
  "title": "PEXPIREAT",
  "summary": "Set the expiration for a key as a UNIX timestamp specified in milliseconds",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.6.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the timeout was set.\n* `0` if the timeout was not set. e.g. key doesn't exist, or operation skipped due to the provided arguments.",
  "history": [
    [
      "7.0",
      "Added options: `NX`, `XX`, `GT` and `LT`."
    ]
  ],
  "syntax": "key milliseconds-timestamp [NX|XX|GT|LT]",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

[PEXPIREAT](/commands/pexpireat) has the same effect and semantic as [EXPIREAT](/commands/expireat), but the Unix time at
which the key will expire is specified in milliseconds instead of seconds.

## Options

The [PEXPIREAT](/commands/pexpireat) command supports a set of options since Redis 7.0:

* `NX` -- Set expiry only when the key has no expiry
* `XX` -- Set expiry only when the key has an existing expiry
* `GT` -- Set expiry only when the new expiry is greater than current one
* `LT` -- Set expiry only when the new expiry is less than current one

A non-volatile key is treated as an infinite TTL for the purpose of `GT` and `LT`.
The `GT`, `LT` and `NX` options are mutually exclusive.

@examples

```cli
SET mykey "Hello"
PEXPIREAT mykey 1555555555005
TTL mykey
PTTL mykey
```

