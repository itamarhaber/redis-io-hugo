{
  "title": "PUBSUB",
  "summary": "Inspect the state of the Pub/Sub subsystem",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) for the CHANNELS subcommand, where N is the number of active channels, and assuming constant time pattern matching (relatively short channels and patterns). O(N) for the NUMSUB subcommand, where N is the number of requested channels. O(1) for the NUMPAT subcommand.",
  "since": "2.8.0",
  "return_summary": "@integer-reply: the number of patterns all the clients are subscribed to.",
  "syntax": "subcommand [argument ...]",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

The PUBSUB command is an introspection command that allows to inspect the
state of the Pub/Sub subsystem. It is composed of subcommands that are
documented separately. The general form is:

    PUBSUB <subcommand> ... args ...

Cluster note: in a Redis Cluster clients can subscribe to every node, and can
also publish to every other node. The cluster will make sure that published
messages are forwarded as needed. That said, [PUBSUB](/commands/pubsub)'s replies in a cluster only
report information from the node's Pub/Sub context, rather than the entire
cluster.

# PUBSUB CHANNELS [pattern]

Lists the currently *active channels*. An active channel is a Pub/Sub channel
with one or more subscribers (not including clients subscribed to patterns).

If no `pattern` is specified, all the channels are listed, otherwise if pattern
is specified only channels matching the specified glob-style pattern are
listed.

# `PUBSUB NUMSUB [channel-1 ... channel-N]`

Returns the number of subscribers (not counting clients subscribed to patterns)
for the specified channels.

# `PUBSUB NUMPAT`

Returns the number of unique patterns that are subscribed to by clients (that are performed using the
[PSUBSCRIBE](/commands/psubscribe) command). Note that this is not the count of clients subscribed
to patterns but the total number of unique patterns all the clients are subscribed to.

