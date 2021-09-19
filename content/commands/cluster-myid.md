{
  "title": "CLUSTER MYID",
  "summary": "Return the node id",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@bulk-string-reply: The node id.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Returns the node's id.

The [CLUSTER MYID](/commands/cluster-myid) command returns the unique, auto-generated identifier that is associated with the connected cluster node.

