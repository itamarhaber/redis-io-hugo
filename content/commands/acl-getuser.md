{
  "title": "ACL GETUSER",
  "summary": "Get the rules for a specific ACL user",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N). Where N is the number of password, command and pattern rules that the user has.",
  "since": "6.0.0",
  "return_summary": "<summary>",
  "history": [
    [
      "6.2",
      "Added Pub/Sub channel patterns."
    ]
  ],
  "syntax": "username",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The command returns all the rules defined for an existing ACL user.

Specifically, it lists the user's ACL flags, password hashes and key name
patterns. Note that command rules are returned as a string in the same
format used with the [ACL SETUSER](/commands/acl-setuser) command. This description of command rules
reflects the user's effective permissions, so while it may not be identical to
the set of rules used to configure the user, it is still functionally identical.

@array-reply: a list of ACL rule definitions for the user.

@examples

Here's the default configuration for the default user:

```
> ACL GETUSER default
1) "flags"
2) 1) "on"
   2) "allkeys"
   3) "allcommands"
   4) "nopass"
3) "passwords"
4) (empty array)
5) "commands"
6) "+@all"
7) "keys"
8) 1) "*"
9) "channels"
10) 1) "*"
```
