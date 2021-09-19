{
  "title": "GETEX",
  "summary": "Get the value of a key and optionally set its expiration",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.2.0",
  "return_summary": "@bulk-string-reply: the value of `key`, or `nil` when `key` does not exist.",
  "syntax": "key [EX seconds|PX milliseconds|EXAT timestamp|PXAT milliseconds-timestamp|PERSIST]",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Get the value of `key` and optionally set its expiration.
[GETEX](/commands/getex) is similar to [GET](/commands/get), but is a write command with additional options.

## Options

The [GETEX](/commands/getex) command supports a set of options that modify its behavior:

* `EX` *seconds* -- Set the specified expire time, in seconds.
* `PX` *milliseconds* -- Set the specified expire time, in milliseconds.
* `EXAT` *timestamp-seconds* -- Set the specified Unix time at which the key will expire, in seconds.
* `PXAT` *timestamp-milliseconds* -- Set the specified Unix time at which the key will expire, in milliseconds.
* [PERSIST](/commands/persist) -- Remove the time to live associated with the key.

@examples

```cli
SET mykey "Hello"
GETEX mykey
TTL mykey
GETEX mykey EX 60
TTL mykey
```

