{
  "title": "PSETEX",
  "summary": "Set the value and expiration in milliseconds of a key",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.6.0",
  "return_summary": "<summary>",
  "syntax": "key milliseconds value",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

[PSETEX](/commands/psetex) works exactly like [SETEX](/commands/setex) with the sole difference that the expire
time is specified in milliseconds instead of seconds.

@examples

```cli
PSETEX mykey 1000 "Hello"
PTTL mykey
GET mykey
```

