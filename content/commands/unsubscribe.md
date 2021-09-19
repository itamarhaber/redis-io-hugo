{
  "title": "UNSUBSCRIBE",
  "summary": "Stop listening for messages posted to the given channels",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of clients already subscribed to a channel.",
  "since": "2.0.0",
  "return_summary": "<summary>",
  "syntax": "[channel ...]",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

Unsubscribes the client from the given channels, or from all of them if none is
given.

When no channels are specified, the client is unsubscribed from all the
previously subscribed channels.
In this case, a message for every unsubscribed channel will be sent to the
client.

