{
  "title": "PUNSUBSCRIBE",
  "summary": "Stop listening for messages posted to channels matching the given patterns",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+M) where N is the number of patterns the client is already subscribed and M is the number of total patterns subscribed in the system (by any client).",
  "since": "2.0.0",
  "return_summary": "<summary>",
  "syntax": "[undefined pattern ...]",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

Unsubscribes the client from the given patterns, or from all of them if none is
given.

When no patterns are specified, the client is unsubscribed from all the
previously subscribed patterns.
In this case, a message for every unsubscribed pattern will be sent to the
client.

