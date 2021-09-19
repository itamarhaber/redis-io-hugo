{
  "title": "GET",
  "summary": "Get the value of a key",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@bulk-string-reply: the value of `key`, or `nil` when `key` does not exist.",
  "syntax": "key",
  "acl_categories": [
    "string",
    "slow"
  ]
}

Get the value of `key`.
If the key does not exist the special value `nil` is returned.
An error is returned if the value stored at `key` is not a string, because [GET](/commands/get)
only handles string values.

@examples

```cli
GET nonexisting
SET mykey "Hello"
GET mykey
```

