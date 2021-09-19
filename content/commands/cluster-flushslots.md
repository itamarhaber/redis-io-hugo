{
  "title": "CLUSTER FLUSHSLOTS",
  "summary": "Delete a node's own slots information",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@simple-string-reply: `OK`",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Deletes all slots from a node.

The [CLUSTER FLUSHSLOTS](/commands/cluster-flushslots) deletes all information about slots from the connected node. It can only be called when the database is empty.

