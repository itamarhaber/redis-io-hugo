{
  "title": "CLIENT UNPAUSE",
  "summary": "Resume processing of clients that were paused",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) Where N is the number of paused clients",
  "since": "6.2.0",
  "return_summary": "@simple-string-reply: The command returns `OK`",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

[CLIENT UNPAUSE](/commands/client-unpause) is used to resume command processing for all clients that were paused by [CLIENT PAUSE](/commands/client-pause).

