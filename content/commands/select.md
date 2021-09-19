{
  "title": "SELECT",
  "summary": "Change the selected database for the current connection",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "index",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

Select the Redis logical database having the specified zero-based numeric index.
New connections always use the database 0.

Selectable Redis databases are a form of namespacing: all databases are still persisted in the same RDB / AOF file. However different databases can have keys with the same name, and commands like [FLUSHDB](/commands/flushdb), [SWAPDB](/commands/swapdb) or [RANDOMKEY](/commands/randomkey) work on specific databases.

In practical terms, Redis databases should be used to separate different keys belonging to the same application (if needed), and not to use a single Redis instance for multiple unrelated applications.

When using Redis Cluster, the [SELECT](/commands/select) command cannot be used, since Redis Cluster only supports database zero. In the case of a Redis Cluster, having multiple databases would be useless and an unnecessary source of complexity. Commands operating atomically on a single database would not be possible with the Redis Cluster design and goals.

Since the currently selected database is a property of the connection, clients should track the currently selected database and re-select it on reconnection. While there is no command in order to query the selected database in the current connection, the [CLIENT LIST](/commands/client-list) output shows, for each client, the currently selected database.
