{
  "title": "BGSAVE",
  "summary": "Asynchronously save the dataset to disk",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply: `Background saving started` if `BGSAVE` started correctly or `Background saving scheduled` when used with the `SCHEDULE` subcommand.",
  "history": [
    [
      "3.2.2",
      "Added the `SCHEDULE` option."
    ]
  ],
  "syntax": "[SCHEDULE]",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Save the DB in background.

Normally the OK code is immediately returned.
Redis forks, the parent continues to serve the clients, the child saves the DB
on disk then exits.

An error is returned if there is already a background save running or if there
is another non-background-save process running, specifically an in-progress AOF
rewrite.

If `BGSAVE SCHEDULE` is used, the command will immediately return `OK` when an
AOF rewrite is in progress and schedule the background save to run at the next
opportunity.

A client may be able to check if the operation succeeded using the [LASTSAVE](/commands/lastsave)
command.

Please refer to the [persistence documentation][tp] for detailed information.

[tp]: /topics/persistence

