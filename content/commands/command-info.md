{
  "title": "COMMAND INFO",
  "summary": "Get array of specific Redis command details",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) when N is number of commands to look up",
  "since": "2.8.13",
  "return_summary": "@array-reply: nested list of command details.",
  "syntax": "command-name ...",
  "acl_categories": [
    "connection",
    "slow"
  ]
}

Returns @array-reply of details about multiple Redis commands.

Same result format as [COMMAND](/commands/command) except you can specify which commands
get returned.

If you request details about non-existing commands, their return
position will be nil.


@examples

```cli
COMMAND INFO get set eval
COMMAND INFO foo evalsha config bar
```

