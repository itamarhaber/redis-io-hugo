{
  "title": "PEXPIRE",
  "summary": "Set a key's time to live in milliseconds",
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
  "syntax": "key milliseconds [NX|XX|GT|LT]",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

This command works exactly like [EXPIRE](/commands/expire) but the time to live of the key is
specified in milliseconds instead of seconds.

## Options

The [PEXPIRE](/commands/pexpire) command supports a set of options since Redis 7.0:

* `NX` -- Set expiry only when the key has no expiry
* `XX` -- Set expiry only when the key has an existing expiry
* `GT` -- Set expiry only when the new expiry is greater than current one
* `LT` -- Set expiry only when the new expiry is less than current one

A non-volatile key is treated as an infinite TTL for the purpose of `GT` and `LT`.
The `GT`, `LT` and `NX` options are mutually exclusive.

@examples

```cli
SET mykey "Hello"
PEXPIRE mykey 1500
TTL mykey
PTTL mykey
PEXPIRE mykey 1000 XX
TTL mykey
PEXPIRE mykey 1000 NX
TTL mykey
```

