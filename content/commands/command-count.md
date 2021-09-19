{
  "title": "COMMAND COUNT",
  "summary": "Get total number of Redis commands",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.8.13",
  "return_summary": "@integer-reply: number of commands returned by `COMMAND`",
  "syntax": "",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

Returns @integer-reply of number of total commands in this Redis server.

@examples

```cli
COMMAND COUNT
```

