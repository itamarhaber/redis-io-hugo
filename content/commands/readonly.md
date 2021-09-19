{
  "title": "READONLY",
  "summary": "Enables read queries for a connection to a cluster replica node",
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

Enables read queries for a connection to a Redis Cluster replica node. 

Normally replica nodes will redirect clients to the authoritative master for
the hash slot involved in a given command, however clients can use replicas
in order to scale reads using the [READONLY](/commands/readonly) command.

[READONLY](/commands/readonly) tells a Redis Cluster replica node that the client is willing to
read possibly stale data and is not interested in running write queries.

When the connection is in readonly mode, the cluster will send a redirection
to the client only if the operation involves keys not served by the replica's
master node. This may happen because:

1. The client sent a command about hash slots never served by the master of this replica.
2. The cluster was reconfigured (for example resharded) and the replica is no longer able to serve commands for a given hash slot.

