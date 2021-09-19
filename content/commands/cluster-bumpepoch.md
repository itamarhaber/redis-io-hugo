{
  "title": "CLUSTER BUMPEPOCH",
  "summary": "Advance the cluster config epoch",
  "group": "cluster",
  "tags": [
    "Command",
    "Cluster"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@simple-string-reply: `BUMPED` if the epoch was incremented, or `STILL` if the node already has the greatest config epoch in the cluster.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Advances the cluster config epoch.

The [CLUSTER BUMPEPOCH](/commands/cluster-bumpepoch) command triggers an increment to the cluster's config epoch from the connected node. The epoch will be incremented if the node's config epoch is zero, or if it is less than the cluster's greatest epoch.

**Note:** config epoch management is performed internally by the cluster, and relies on obtaining a consensus of nodes. The [CLUSTER BUMPEPOCH](/commands/cluster-bumpepoch) attempts to increment the config epoch **WITHOUT** getting the consensus, so using it may violate the "last failover wins" rule. Use it with caution.

