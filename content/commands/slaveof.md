{
  "title": "SLAVEOF",
  "summary": "Make the server a replica of another instance, or promote it as master. Deprecated starting with Redis 5. Use REPLICAOF instead.",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "host port",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

**A note about the word slave used in this man page and command name**: Starting with Redis 5 this command: starting with Redis version 5, if not for backward compatibility, the Redis project no longer uses the word slave. Please use the new command [REPLICAOF](/commands/replicaof). The command [SLAVEOF](/commands/slaveof) will continue to work for backward compatibility.

The [SLAVEOF](/commands/slaveof) command can change the replication settings of a replica on the fly.
If a Redis server is already acting as replica, the command [SLAVEOF](/commands/slaveof) NO ONE will
turn off the replication, turning the Redis server into a MASTER.
In the proper form [SLAVEOF](/commands/slaveof) hostname port will make the server a replica of
another server listening at the specified hostname and port.

If a server is already a replica of some master, [SLAVEOF](/commands/slaveof) hostname port will stop
the replication against the old server and start the synchronization against the
new one, discarding the old dataset.

The form [SLAVEOF](/commands/slaveof) NO ONE will stop replication, turning the server into a
MASTER, but will not discard the replication.
So, if the old master stops working, it is possible to turn the replica into a
master and set the application to use this new master in read/write.
Later when the other Redis server is fixed, it can be reconfigured to work as a
replica.

