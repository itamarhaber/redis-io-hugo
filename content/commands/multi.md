{
  "title": "MULTI",
  "summary": "Mark the start of a transaction block",
  "group": "transactions",
  "tags": [
    "Command",
    "Transactions"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.2.0",
  "return_summary": "@simple-string-reply: always `OK`.",
  "syntax": "",
  "acl_categories": [
    "transaction",
    "slow"
  ]
}

Marks the start of a [transaction][tt] block.
Subsequent commands will be queued for atomic execution using [EXEC](/commands/exec).

[tt]: /topics/transactions

