{
  "title": "PSUBSCRIBE",
  "summary": "Listen for messages published to channels matching the given patterns",
  "group": "pubsub",
  "tags": [
    "Command",
    "Pubsub"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of patterns the client is already subscribed to.",
  "since": "2.0.0",
  "return_summary": "<summary>",
  "syntax": "undefined pattern ...",
  "acl_categories": [
    "pubsub",
    "slow"
  ]
}

Subscribes the client to the given patterns.

Supported glob-style patterns:

* `h?llo` subscribes to `hello`, `hallo` and `hxllo`
* `h*llo` subscribes to `hllo` and `heeeello`
* `h[ae]llo` subscribes to `hello` and `hallo,` but not `hillo`

Use `\` to escape special characters if you want to match them verbatim.

