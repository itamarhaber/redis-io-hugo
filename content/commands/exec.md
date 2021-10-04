Executes all previously queued commands in a [transaction][tt] and restores the
connection state to normal.

[tt]: /topics/transactions

When using [WATCH](/commands/watch), [EXEC](/commands/exec) will execute commands only if the watched keys were
not modified, allowing for a [check-and-set mechanism][ttc].

[ttc]: /topics/transactions#cas

