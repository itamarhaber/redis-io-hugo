{
  "title": "LASTSAVE",
  "summary": "Get the UNIX time stamp of the last successful save to disk",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@integer-reply: an UNIX time stamp.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Return the UNIX TIME of the last DB save executed with success.
A client may check if a [BGSAVE](/commands/bgsave) command succeeded reading the [LASTSAVE](/commands/lastsave) value,
then issuing a [BGSAVE](/commands/bgsave) command and checking at regular intervals every N
seconds if [LASTSAVE](/commands/lastsave) changed.

