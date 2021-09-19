{
  "title": "PEXPIRETIME",
  "summary": "Get the expiration Unix timestamp for a key in milliseconds",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "7.0.0",
  "return_summary": "@integer-reply: Expiration Unix timestamp in milliseconds, or a negative value in order to signal an error (see the description below).\n* The command returns `-1` if the key exists but has no associated expiration time.\n* The command returns `-2` if the key does not exist.",
  "syntax": "key",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

[PEXPIRETIME](/commands/pexpiretime) has the same semantic as [EXPIRETIME](/commands/expiretime), but returns the absolute Unix expiration timestamp in milliseconds instead of seconds.

@examples

```cli
SET mykey "Hello"
PEXPIREAT mykey 33177117420000
PEXPIRETIME mykey
```

