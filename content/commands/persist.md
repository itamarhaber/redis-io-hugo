{
  "title": "PERSIST",
  "summary": "Remove the expiration from a key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.2.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the timeout was removed.\n* `0` if `key` does not exist or does not have an associated timeout.",
  "syntax": "key",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

Remove the existing timeout on `key`, turning the key from _volatile_ (a key
with an expire set) to _persistent_ (a key that will never expire as no timeout
is associated).

@examples

```cli
SET mykey "Hello"
EXPIRE mykey 10
TTL mykey
PERSIST mykey
TTL mykey
```

