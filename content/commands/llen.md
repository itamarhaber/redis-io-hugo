{
  "title": "LLEN",
  "summary": "Get the length of a list",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the length of the list at `key`.",
  "syntax": "key",
  "acl_categories": [
    "list",
    "slow"
  ]
}

Returns the length of the list stored at `key`.
If `key` does not exist, it is interpreted as an empty list and `0` is returned.
An error is returned when the value stored at `key` is not a list.

@examples

```cli
LPUSH mylist "World"
LPUSH mylist "Hello"
LLEN mylist
```

