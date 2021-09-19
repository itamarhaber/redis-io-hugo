{
  "title": "DUMP",
  "summary": "Return a serialized version of the value stored at the specified key.",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) to access the key and additional O(N*M) to serialize it, where N is the number of Redis objects composing the value and M their average size. For small string values the time complexity is thus O(1)+O(1*M) where M is small, so simply O(1).",
  "since": "2.6.0",
  "return_summary": "@bulk-string-reply: the serialized value.",
  "syntax": "key",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Serialize the value stored at key in a Redis-specific format and return it to
the user.
The returned value can be synthesized back into a Redis key using the [RESTORE](/commands/restore)
command.

The serialization format is opaque and non-standard, however it has a few
semantic characteristics:

* It contains a 64-bit checksum that is used to make sure errors will be
  detected.
  The [RESTORE](/commands/restore) command makes sure to check the checksum before synthesizing a
  key using the serialized value.
* Values are encoded in the same format used by RDB.
* An RDB version is encoded inside the serialized value, so that different Redis
  versions with incompatible RDB formats will refuse to process the serialized
  value.

The serialized value does NOT contain expire information.
In order to capture the time to live of the current value the [PTTL](/commands/pttl) command
should be used.

If `key` does not exist a nil bulk reply is returned.

@examples

```cli
SET mykey 10
DUMP mykey
```

