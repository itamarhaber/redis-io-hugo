{
  "title": "REPLICAOF",
  "summary": "Make the server a replica of another instance, or promote it as master.",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "5.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "host port",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The [REPLICAOF](/commands/replicaof) command can change the replication settings of a replica on the fly.

If a Redis server is already acting as replica, the command [REPLICAOF](/commands/replicaof) NO ONE will turn off the replication, turning the Redis server into a MASTER.  In the proper form [REPLICAOF](/commands/replicaof) hostname port will make the server a replica of another server listening at the specified hostname and port.

If a server is already a replica of some master, [REPLICAOF](/commands/replicaof) hostname port will stop the replication against the old server and start the synchronization against the new one, discarding the old dataset.

The form [REPLICAOF](/commands/replicaof) NO ONE will stop replication, turning the server into a MASTER, but will not discard the replication. So, if the old master stops working, it is possible to turn the replica into a master and set the application to use this new master in read/write. Later when the other Redis server is fixed, it can be reconfigured to work as a replica.

