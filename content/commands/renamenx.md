{
  "title": "RENAMENX",
  "summary": "Rename a key, only if the new key does not exist",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if `key` was renamed to `newkey`.\n* `0` if `newkey` already exists.",
  "syntax": "key newkey",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

Renames `key` to `newkey` if `newkey` does not yet exist.
It returns an error when `key` does not exist.

In Cluster mode, both `key` and `newkey` must be in the same **hash slot**, meaning that in practice only keys that have the same hash tag can be reliably renamed in cluster.


@examples

```cli
SET mykey "Hello"
SET myotherkey "World"
RENAMENX mykey myotherkey
GET myotherkey
```

