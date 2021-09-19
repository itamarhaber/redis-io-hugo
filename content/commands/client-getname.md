{
  "title": "CLIENT GETNAME",
  "summary": "Get the current connection name",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.6.9",
  "return_summary": "@bulk-string-reply: The connection name, or a null bulk reply if no name is set.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

The [CLIENT GETNAME](/commands/client-getname) returns the name of the current connection as set by [CLIENT SETNAME](/commands/client-setname). Since every new connection starts without an associated name, if no name was assigned a null bulk reply is returned.

