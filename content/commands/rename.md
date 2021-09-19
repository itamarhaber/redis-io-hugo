{
  "title": "RENAME",
  "summary": "Rename a key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "key newkey",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

Renames `key` to `newkey`.
It returns an error when `key` does not exist.
If `newkey` already exists it is overwritten, when this happens [RENAME](/commands/rename) executes an implicit [DEL](/commands/del) operation, so if the deleted key contains a very big value it may cause high latency even if [RENAME](/commands/rename) itself is usually a constant-time operation.

In Cluster mode, both `key` and `newkey` must be in the same **hash slot**, meaning that in practice only keys that have the same hash tag can be reliably renamed in cluster.

@examples

```cli
SET mykey "Hello"
RENAME mykey myotherkey
GET myotherkey
```

