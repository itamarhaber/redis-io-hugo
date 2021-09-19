{
  "title": "ACL LOG",
  "summary": "List latest events denied because of ACLs in place",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the number of entries shown.",
  "since": "6.0.0",
  "return_summary": "When called to show security events:\n\n@array-reply: a list of ACL security events.\n\nWhen called with `RESET`:\n\n@simple-string-reply: `OK` if the security log was cleared.",
  "syntax": "[count or RESET]",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The command shows a list of recent ACL security events:

1. Failures to authenticate their connections with [AUTH](/commands/auth) or [HELLO](/commands/hello).
2. Commands denied because against the current ACL rules.
3. Commands denied because accessing keys not allowed in the current ACL rules.

The optional argument specifies how many entries to show. By default
up to ten failures are returned. The special [RESET](/commands/reset) argument clears the log.
Entries are displayed starting from the most recent.

@examples

```
> AUTH someuser wrongpassword
(error) WRONGPASS invalid username-password pair
> ACL LOG 1
1)  1) "count"
    2) (integer) 1
    3) "reason"
    4) "auth"
    5) "context"
    6) "toplevel"
    7) "object"
    8) "AUTH"
    9) "username"
   10) "someuser"
   11) "age-seconds"
   12) "4.0960000000000001"
   13) "client-info"
   14) "id=6 addr=127.0.0.1:63026 fd=8 name= age=9 idle=0 flags=N db=0 sub=0 psub=0 multi=-1 qbuf=48 qbuf-free=32720 obl=0 oll=0 omem=0 events=r cmd=auth user=default"
```

