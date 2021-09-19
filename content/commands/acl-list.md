{
  "title": "ACL LIST",
  "summary": "List the current ACL rules in ACL config file format",
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

The command shows the currently active ACL rules in the Redis server. Each
line in the returned array defines a different user, and the format is the
same used in the redis.conf file or the external ACL file, so you can
cut and paste what is returned by the ACL LIST command directly inside a
configuration file if you wish (but make sure to check [ACL SAVE](/commands/acl-save)).

@examples

```
> ACL LIST
1) "user antirez on #9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08 ~objects:* &* +@all -@admin -@dangerous"
2) "user default on nopass ~* &* +@all"
```

