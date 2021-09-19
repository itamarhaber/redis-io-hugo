{
  "title": "ACL USERS",
  "summary": "List the username of all the configured ACL rules",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N). Where N is the number of configured users.",
  "since": "6.0.0",
  "return_summary": "An array of strings.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The command shows a list of all the usernames of the currently configured
users in the Redis ACL system.

@examples

```
> ACL USERS
1) "anna"
2) "antirez"
3) "default"
```

