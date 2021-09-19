{
  "title": "CLUSTER REPLICAS",
  "summary": "List replica nodes of the specified master node",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "5.0.0",
  "return_summary": "The command returns data in the same format as `CLUSTER NODES`.",
  "syntax": "node-id",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The command provides a list of replica nodes replicating from the specified
master node. The list is provided in the same format used by [CLUSTER NODES](/commands/cluster-nodes) (please refer to its documentation for the specification of the format).

The command will fail if the specified node is not known or if it is not
a master according to the node table of the node receiving the command.

Note that if a replica is added, moved, or removed from a given master node,
and we ask [CLUSTER REPLICAS](/commands/cluster-replicas) to a node that has not yet received the
configuration update, it may show stale information. However eventually
(in a matter of seconds if there are no network partitions) all the nodes
will agree about the set of nodes associated with a given master.

