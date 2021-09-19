{
  "title": "EXEC",
  "summary": "Execute all commands issued after MULTI",
  "group": "transactions",
  "tags": [
    "Command",
    "Transactions"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.2.0",
  "return_summary": "@array-reply: each element being the reply to each of the commands in the\natomic transaction.\n\nWhen using `WATCH`, `EXEC` can return a @nil-reply if the execution was aborted.",
  "syntax": "",
  "acl_categories": [
    "transaction",
    "slow"
  ]
}

Executes all previously queued commands in a [transaction][tt] and restores the
connection state to normal.

[tt]: /topics/transactions

When using [WATCH](/commands/watch), [EXEC](/commands/exec) will execute commands only if the watched keys were
not modified, allowing for a [check-and-set mechanism][ttc].

[ttc]: /topics/transactions#cas

