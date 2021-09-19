{
  "title": "ACL WHOAMI",
  "summary": "Return the name of the user associated to the current connection",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.0.0",
  "return_summary": "@bulk-string-reply: the username of the current connection.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Return the username the current connection is authenticated with.
New connections are authenticated with the "default" user. They
can change user using [AUTH](/commands/auth).

@examples

```
> ACL WHOAMI
"default"
```

