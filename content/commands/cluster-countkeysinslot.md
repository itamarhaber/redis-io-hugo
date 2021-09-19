{
  "title": "CLUSTER COUNTKEYSINSLOT",
  "summary": "Return the number of local keys in the specified hash slot",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@integer-reply: The number of keys in the specified hash slot, or an error if the hash slot is invalid.",
  "syntax": "slot",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Returns the number of keys in the specified Redis Cluster hash slot. The
command only queries the local data set, so contacting a node
that is not serving the specified hash slot will always result in a count of
zero being returned.

```
> CLUSTER COUNTKEYSINSLOT 7000
(integer) 50341
```

