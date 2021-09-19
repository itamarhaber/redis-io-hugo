{
  "title": "WATCH",
  "summary": "Watch the given keys to determine execution of the MULTI/EXEC block",
  "group": "transactions",
  "tags": [
    "Command",
    "Transactions"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for every key.",
  "since": "2.2.0",
  "return_summary": "@simple-string-reply: always `OK`.",
  "syntax": "key ...",
  "acl_categories": [
    "transaction",
    "slow"
  ]
}

Marks the given keys to be watched for conditional execution of a
[transaction][tt].

[tt]: /topics/transactions

