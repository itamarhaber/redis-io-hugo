{
  "title": "DISCARD",
  "summary": "Discard all commands issued after MULTI",
  "group": "transactions",
  "tags": [
    "Command",
    "Transactions"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "2.0.0",
  "return_summary": "@simple-string-reply: always `OK`.",
  "syntax": "",
  "acl_categories": [
    "transaction",
    "slow"
  ]
}

Flushes all previously queued commands in a [transaction][tt] and restores the
connection state to normal.

[tt]: /topics/transactions

If [WATCH](/commands/watch) was used, [DISCARD](/commands/discard) unwatches all keys watched by the connection.

