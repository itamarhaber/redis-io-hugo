{
  "title": "RESET",
  "summary": "Reset the connection",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "6.2",
  "return_summary": "@simple-string-reply: always 'RESET'.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

This command performs a full reset of the connection's server-side context, 
mimicking the effect of disconnecting and reconnecting again.

When the command is called from a regular client connection, it does the
following:

* Discards the current [MULTI](/commands/multi) transaction block, if one exists.
* Unwatches all keys [WATCH](/commands/watch)ed by the connection.
* Disables [CLIENT TRACKING](/commands/client-tracking), if in use.
* Sets the connection to [READWRITE](/commands/readwrite) mode.
* Cancels the connection's [ASKING](/commands/asking) mode, if previously set.
* Sets [CLIENT REPLY](/commands/client-reply) to `ON`.
* Sets the protocol version to RESP2.
* [SELECT](/commands/select)s database 0.
* Exits [MONITOR](/commands/monitor) mode, when applicable.
* Aborts Pub/Sub's subscription state ([SUBSCRIBE](/commands/subscribe) and [PSUBSCRIBE](/commands/psubscribe)), when
  appropriate.
* Deauthenticates the connection, requiring a call [AUTH](/commands/auth) to reauthenticate when
  authentication is enabled.

