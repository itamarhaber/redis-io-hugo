Flushes all previously queued commands in a [transaction][tt] and restores the
connection state to normal.

[tt]: /topics/transactions

If [WATCH](/commands/watch) was used, [DISCARD](/commands/discard) unwatches all keys watched by the connection.

