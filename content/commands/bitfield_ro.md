{
  "title": "BITFIELD_RO",
  "summary": "Perform arbitrary bitfield integer operations on strings. Read-only variant of BITFIELD",
  "group": "bitmap",
  "tags": [
    "Command",
    "Bitmap"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each subcommand specified",
  "since": "6.2.0",
  "return_summary": "@array-reply: An array with each entry being the corresponding result of the subcommand given at the same position.",
  "syntax": "key GET type offset",
  "acl_categories": [
    "bitmap",
    "slow"
  ]
}

Read-only variant of the [BITFIELD](/commands/bitfield) command.
It is like the original [BITFIELD](/commands/bitfield) but only accepts `GET` subcommand and can safely be used in read-only replicas.

Since the original [BITFIELD](/commands/bitfield) has `SET` and `!INCRBY` options it is technically flagged as a writing command in the Redis command table.
For this reason read-only replicas in a Redis Cluster will redirect it to the master instance even if the connection is in read-only mode (see the [READONLY](/commands/readonly) command of Redis Cluster).

Since Redis 6.2, the [BITFIELD_RO](/commands/bitfield_ro) variant was introduced in order to allow [BITFIELD](/commands/bitfield) behavior in read-only replicas without breaking compatibility on command flags.

See original [BITFIELD](/commands/bitfield) for more details.

@examples

```
BITFIELD_RO hello GET i8 16
```

