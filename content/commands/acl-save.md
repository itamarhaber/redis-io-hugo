{
  "title": "ACL SAVE",
  "summary": "Save the current ACL rules in the configured ACL file",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N). Where N is the number of configured users.",
  "since": "6.0.0",
  "return_summary": "@simple-string-reply: `OK` on success.\n\nThe command may fail with an error for several reasons: if the file cannot be written or if the server is not configured to use an external ACL file.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

When Redis is configured to use an ACL file (with the `aclfile` configuration
option), this command will save the currently defined ACLs from the server memory to the ACL file.

@examples

```
> ACL SAVE
+OK

> ACL SAVE
-ERR There was an error trying to save the ACLs. Please check the server logs for more information
```

