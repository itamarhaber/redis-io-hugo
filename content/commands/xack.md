{
  "title": "XACK",
  "summary": "Marks a pending message as correctly processed, effectively removing it from the pending entries list of the consumer group. Return value of the command is the number of messages successfully acknowledged, that is, the IDs we were actually able to resolve in the PEL.",
  "group": "stream",
  "tags": [
    "Command",
    "Stream"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each message ID processed.",
  "since": "5.0.0",
  "return_summary": "@integer-reply, specifically:\n\nThe command returns the number of messages successfully acknowledged.\nCertain message IDs may no longer be part of the PEL (for example because\nthey have already been acknowledged), and XACK will not count them as\nsuccessfully acknowledged.",
  "syntax": "key group ID ...",
  "acl_categories": [
    "stream",
    "write",
    "slow"
  ]
}

The [XACK](/commands/xack) command removes one or multiple messages from the
*Pending Entries List* (PEL) of a stream consumer group. A message is pending,
and as such stored inside the PEL, when it was delivered to some consumer,
normally as a side effect of calling [XREADGROUP](/commands/xreadgroup), or when a consumer took
ownership of a message calling [XCLAIM](/commands/xclaim). The pending message was delivered to
some consumer but the server is yet not sure it was processed at least once.
So new calls to [XREADGROUP](/commands/xreadgroup) to grab the messages history for a consumer
(for instance using an ID of 0), will return such message.
Similarly the pending message will be listed by the [XPENDING](/commands/xpending) command,
that inspects the PEL.

Once a consumer *successfully* processes a message, it should call [XACK](/commands/xack)
so that such message does not get processed again, and as a side effect,
the PEL entry about this message is also purged, releasing memory from the
Redis server.

@examples

```
redis> XACK mystream mygroup 1526569495631-0
(integer) 1
```

