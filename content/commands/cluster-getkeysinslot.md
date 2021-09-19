{
  "title": "CLUSTER GETKEYSINSLOT",
  "summary": "Return local key names in the specified hash slot",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)) where N is the number of requested keys",
  "since": "3.0.0",
  "return_summary": "@array-reply: From 0 to *count* key names in a Redis array reply.",
  "syntax": "slot count",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The command returns an array of keys names stored in the contacted node and
hashing to the specified hash slot. The maximum number of keys to return
is specified via the `count` argument, so that it is possible for the user
of this API to batch-processing keys.

The main usage of this command is during rehashing of cluster slots from one
node to another. The way the rehashing is performed is exposed in the Redis
Cluster specification, or in a more simple to digest form, as an appendix
of the [CLUSTER SETSLOT](/commands/cluster-setslot) command documentation.

```
> CLUSTER GETKEYSINSLOT 7000 3
"47344|273766|70329104160040|key_39015"
"47344|273766|70329104160040|key_89793"
"47344|273766|70329104160040|key_92937"
```

