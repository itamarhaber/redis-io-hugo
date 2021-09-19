{
  "title": "GETDEL",
  "summary": "Get the value of a key and delete the key",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.2.0",
  "return_summary": "@bulk-string-reply: the value of `key`, `nil` when `key` does not exist, or an error if the key's value type isn't a string.",
  "syntax": "key",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Get the value of `key` and delete the key.
This command is similar to [GET](/commands/get), except for the fact that it also deletes the key on success (if and only if the key's value type is a string).

@examples

```cli
SET mykey "Hello"
GETDEL mykey
GET mykey
```

