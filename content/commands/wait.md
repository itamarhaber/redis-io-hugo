{
  "title": "WAIT",
  "summary": "Wait for the synchronous replication of all the write commands sent in the context of the current connection",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.0.0",
  "return_summary": "@integer-reply: The command returns the number of replicas reached by all the writes performed in the context of the current connection.",
  "syntax": "numreplicas timeout",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

This command blocks the current client until all the previous write commands
are successfully transferred and acknowledged by at least the specified number
of replicas. If the timeout, specified in milliseconds, is reached, the command
returns even if the specified number of replicas were not yet reached.

The command **will always return** the number of replicas that acknowledged
the write commands sent before the [WAIT](/commands/wait) command, both in the case where
the specified number of replicas are reached, or when the timeout is reached.

A few remarks:

1. When [WAIT](/commands/wait) returns, all the previous write commands sent in the context of the current connection are guaranteed to be received by the number of replicas returned by [WAIT](/commands/wait).
2. If the command is sent as part of a [MULTI](/commands/multi) transaction, the command does not block but instead just return ASAP the number of replicas that acknowledged the previous write commands.
3. A timeout of 0 means to block forever.
4. Since [WAIT](/commands/wait) returns the number of replicas reached both in case of failure and success, the client should check that the returned value is equal or greater to the replication level it demanded.

Consistency and WAIT
---

Note that [WAIT](/commands/wait) does not make Redis a strongly consistent store: while synchronous replication is part of a replicated state machine, it is not the only thing needed. However in the context of Sentinel or Redis Cluster failover, [WAIT](/commands/wait) improves the real world data safety.

Specifically if a given write is transferred to one or more replicas, it is more likely (but not guaranteed) that if the master fails, we'll be able to promote, during a failover, a replica that received the write: both Sentinel and Redis Cluster will do a best-effort attempt to promote the best replica among the set of available replicas.

However this is just a best-effort attempt so it is possible to still lose a write synchronously replicated to multiple replicas.

Implementation details
---

Since the introduction of partial resynchronization with replicas (PSYNC feature) Redis replicas asynchronously ping their master with the offset they already processed in the replication stream. This is used in multiple ways:

1. Detect timed out replicas.
2. Perform a partial resynchronization after a disconnection.
3. Implement [WAIT](/commands/wait).

In the specific case of the implementation of [WAIT](/commands/wait), Redis remembers, for each client, the replication offset of the produced replication stream when a given
write command was executed in the context of a given client. When [WAIT](/commands/wait) is
called Redis checks if the specified number of replicas already acknowledged
this offset or a greater one.

@examples

```
> SET foo bar
OK
> WAIT 1 0
(integer) 1
> WAIT 2 1000
(integer) 1
```

In the following example the first call to [WAIT](/commands/wait) does not use a timeout and asks for the write to reach 1 replica. It returns with success. In the second attempt instead we put a timeout, and ask for the replication of the write to two replicas. Since there is a single replica available, after one second [WAIT](/commands/wait) unblocks and returns 1, the number of replicas reached.

