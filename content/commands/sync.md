{
  "title": "SYNC",
  "summary": "Internal command used for replication",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "**Non standard return value**, a bulk transfer of the data followed by `PING` and write requests from the master.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Initiates a replication stream from the master.

The [SYNC](/commands/sync) command is called by Redis replicas for initiating a replication
stream from the master. It has been replaced in newer versions of Redis by
 [PSYNC](/commands/psync).

For more information about replication in Redis please check the
[replication page][tr].

[tr]: /topics/replication

