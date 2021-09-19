{
  "title": "ACL DELUSER",
  "summary": "Remove the specified ACL users and the associated rules",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) amortized time considering the typical user.",
  "since": "6.0.0",
  "return_summary": "@integer-reply: The number of users that were deleted. This number will not always match the number of arguments since certain users may not exist.",
  "syntax": "username ...",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Delete all the specified ACL users and terminate all the connections that are
authenticated with such users. Note: the special `default` user cannot be
removed from the system, this is the default user that every new connection
is authenticated with. The list of users may include usernames that do not
exist, in such case no operation is performed for the non existing users.

@examples

```
> ACL DELUSER antirez
1
```

