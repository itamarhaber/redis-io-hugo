{
  "title": "DEBUG SEGFAULT",
  "summary": "Make the server crash",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

[DEBUG SEGFAULT](/commands/debug-segfault) performs an invalid memory access that crashes Redis.
It is used to simulate bugs during the development.

