{
  "title": "STRLEN",
  "summary": "Get the length of the value stored in a key",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.2.0",
  "return_summary": "@integer-reply: the length of the string at `key`, or `0` when `key` does not\nexist.",
  "syntax": "key",
  "acl_categories": [
    "string",
    "slow"
  ]
}

Returns the length of the string value stored at `key`.
An error is returned when `key` holds a non-string value.

@examples

```cli
SET mykey "Hello world"
STRLEN mykey
STRLEN nonexisting
```

