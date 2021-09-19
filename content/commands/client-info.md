{
  "title": "CLIENT INFO",
  "summary": "Returns information about the current client connection.",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.2.0",
  "return_summary": "@bulk-string-reply: a unique string, as described at the `CLIENT LIST` page, for the current client.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

The command returns information and statistics about the current client connection in a mostly human readable format.

The reply format is identical to that of [CLIENT LIST](/commands/client-list), and the content consists only of information about the current client.

@examples

```cli
CLIENT INFO
```

