{
  "title": "PUBLISH",
  "summary": "Post a message to a channel",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+M) where N is the number of clients subscribed to the receiving channel and M is the total number of subscribed patterns (by any client).",
  "since": "2.0.0",
  "return_summary": "@integer-reply: the number of clients that received the message. Note that in a\nRedis Cluster, only clients that are connected to the same node as the\npublishing client are included in the count.",
  "syntax": "channel message",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

Posts a message to the given channel.

In a Redis Cluster clients can publish to every node. The cluster makes sure
that published messages are forwarded as needed, so clients can subscribe to any
channel by connecting to any one of the nodes.

