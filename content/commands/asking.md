{
  "title": "ASKING",
  "summary": "Sent by cluster clients after an -ASK redirect",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@simple-string-reply: `OK`.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

When a cluster client receives an `-ASK` redirect, the [ASKING](/commands/asking) command is sent to the target node followed by the command which was redirected.
This is normally done automatically by cluster clients.

If an `-ASK` redirect is received during a transaction, only one ASKING command needs to be sent to the target node before sending the complete transaction to the target node.

See [ASK redirection in the Redis Cluster Specification](/topics/cluster-spec#ask-redirection) for details.

