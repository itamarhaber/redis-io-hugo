{
  "title": "UNWATCH",
  "summary": "Forget about all watched keys",
  "group": "transactions",
  "tags": [
    "Command",
    "Transactions"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.2.0",
  "return_summary": "@simple-string-reply: always `OK`.",
  "syntax": "",
  "acl_categories": [
    "transaction",
    "slow"
  ]
}

Flushes all the previously watched keys for a [transaction][tt].

[tt]: /topics/transactions

If you call [EXEC](/commands/exec) or [DISCARD](/commands/discard), there's no need to manually call [UNWATCH](/commands/unwatch).

