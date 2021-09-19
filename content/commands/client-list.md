{
  "title": "CLIENT LIST",
  "summary": "Get the list of client connections",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of client connections",
  "since": "2.4.0",
  "return_summary": "@bulk-string-reply: a unique string, formatted as follows:\n\n* One client connection per line (separated by LF)\n* Each line is composed of a succession of `property=value` fields separated\n  by a space character.\n\nHere is the meaning of the fields:\n\n* `id`: an unique 64-bit client ID.\n* `name`: the name set by the client with `CLIENT SETNAME`\n* `addr`: address/port of the client\n* `laddr`: address/port of local address client connected to (bind address)\n* `fd`: file descriptor corresponding to the socket\n* `age`: total duration of the connection in seconds\n* `idle`: idle time of the connection in seconds\n* `flags`: client flags (see below)\n* `db`: current database ID\n* `sub`: number of channel subscriptions\n* `psub`: number of pattern matching subscriptions\n* `multi`: number of commands in a MULTI/EXEC context\n* `qbuf`: query buffer length (0 means no query pending)\n* `qbuf-free`: free space of the query buffer (0 means the buffer is full)\n* `obl`: output buffer length\n* `oll`: output list length (replies are queued in this list when the buffer is full)\n* `omem`: output buffer memory usage\n* `events`: file descriptor events (see below)\n* `cmd`: last command played\n* `argv-mem`: incomplete arguments for the next command (already extracted from query buffer)\n* `tot-mem`: total memory consumed by this client in its various buffers\n* `redir`: client id of current client tracking redirection\n* `user`: the authenticated username of the client\n\nThe client flags can be a combination of:\n\n```\nA: connection to be closed ASAP\nb: the client is waiting in a blocking operation\nc: connection to be closed after writing entire reply\nd: a watched keys has been modified - EXEC will fail\ni: the client is waiting for a VM I/O (deprecated)\nM: the client is a master\nN: no specific flag set\nO: the client is a client in MONITOR mode\nP: the client is a Pub/Sub subscriber\nr: the client is in readonly mode against a cluster node\nS: the client is a replica node connection to this instance\nu: the client is unblocked\nU: the client is connected via a Unix domain socket\nx: the client is in a MULTI/EXEC context\nt: the client enabled keys tracking in order to perform client side caching\nR: the client tracking target client is invalid\nB: the client enabled broadcast tracking mode \n```\n\nThe file descriptor events can be:\n\n```\nr: the client socket is readable (event loop)\nw: the client socket is writable (event loop)\n```",
  "history": [
    [
      "2.8.12",
      "Added unique client `id` field."
    ],
    [
      "5.0",
      "Added optional `TYPE` filter."
    ],
    [
      "6.2",
      "Added `laddr` field and the optional `ID` filter."
    ]
  ],
  "syntax": "[TYPE] [ID client-id ...]",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

The [CLIENT LIST](/commands/client-list) command returns information and statistics about the client
connections server in a mostly human readable format.

You can use one of the optional subcommands to filter the list. The `TYPE type` subcommand filters the list by clients' type, where *type* is one of `normal`, `master`, `replica`, and `pubsub`. Note that clients blocked by the [MONITOR](/commands/monitor) command belong to the `normal` class.

The `ID` filter only returns entries for clients with IDs matching the `client-id` arguments.

## Notes

New fields are regularly added for debugging purpose. Some could be removed
in the future. A version safe Redis client using this command should parse
the output accordingly (i.e. handling gracefully missing fields, skipping
unknown fields).

