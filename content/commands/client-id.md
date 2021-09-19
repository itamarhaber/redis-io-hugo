{
  "title": "CLIENT ID",
  "summary": "Returns the client ID for the current connection",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "5.0.0",
  "return_summary": "@integer-reply\n\nThe id of the client.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

The command just returns the ID of the current connection. Every connection
ID has certain guarantees:

1. It is never repeated, so if [CLIENT ID](/commands/client-id) returns the same number, the caller can be sure that the underlying client did not disconnect and reconnect the connection, but it is still the same connection.
2. The ID is monotonically incremental. If the ID of a connection is greater than the ID of another connection, it is guaranteed that the second connection was established with the server at a later time.

This command is especially useful together with [CLIENT UNBLOCK](/commands/client-unblock) which was
introduced also in Redis 5 together with [CLIENT ID](/commands/client-id). Check the [CLIENT UNBLOCK](/commands/client-unblock) command page for a pattern involving the two commands.

@examples

```cli
CLIENT ID
```

