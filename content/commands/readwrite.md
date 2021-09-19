{
  "title": "READWRITE",
  "summary": "Disables read queries for a connection to a cluster replica node",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

Disables read queries for a connection to a Redis Cluster slave node.

Read queries against a Redis Cluster slave node are disabled by default,
but you can use the [READONLY](/commands/readonly) command to change this behavior on a per-
connection basis. The [READWRITE](/commands/readwrite) command resets the readonly mode flag
of a connection back to readwrite.

