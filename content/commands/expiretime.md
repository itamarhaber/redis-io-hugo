{
  "title": "EXPIRETIME",
  "summary": "Get the expiration Unix timestamp for a key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "7.0.0",
  "return_summary": "@integer-reply: Expiration Unix timestamp in seconds, or a negative value in order to signal an error (see the description below).\n* The command returns `-1` if the key exists but has no associated expiration time.\n* The command returns `-2` if the key does not exist.",
  "syntax": "key",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Returns the absolute Unix timestamp (since January 1, 1970) in seconds at which the given key will expire.

See also the [PEXPIRETIME](/commands/pexpiretime) command which returns the same information with milliseconds resolution.

@examples

```cli
SET mykey "Hello"
EXPIREAT mykey 33177117420
EXPIRETIME mykey
```

