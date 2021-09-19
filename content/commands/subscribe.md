{
  "title": "SUBSCRIBE",
  "summary": "Listen for messages published to the given channels",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of channels to subscribe to.",
  "since": "2.0.0",
  "return_summary": "<summary>",
  "history": [
    [
      "6.2",
      "`RESET` can be called to exit subscribed state."
    ]
  ],
  "syntax": "channel ...",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

Subscribes the client to the specified channels.

Once the client enters the subscribed state it is not supposed to issue any
other commands, except for additional [SUBSCRIBE](/commands/subscribe), [PSUBSCRIBE](/commands/psubscribe), [UNSUBSCRIBE](/commands/unsubscribe),
[PUNSUBSCRIBE](/commands/punsubscribe), [PING](/commands/ping), [RESET](/commands/reset) and [QUIT](/commands/quit) commands.

