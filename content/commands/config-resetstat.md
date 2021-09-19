{
  "title": "CONFIG RESETSTAT",
  "summary": "Reset the stats returned by INFO",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@simple-string-reply: always `OK`.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Resets the statistics reported by Redis using the [INFO](/commands/info) command.

These are the counters that are reset:

* Keyspace hits
* Keyspace misses
* Number of commands processed
* Number of connections received
* Number of expired keys
* Number of rejected connections
* Latest fork(2) time
* The `aof_delayed_fsync` counter

