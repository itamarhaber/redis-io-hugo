{
  "title": "RPUSHX",
  "summary": "Append an element to a list, only if the list exists",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each element added, so O(N) to add N elements when the command is called with multiple arguments.",
  "since": "2.2.0",
  "return_summary": "@integer-reply: the length of the list after the push operation.",
  "history": [
    [
      "4.0",
      "Accepts multiple `element` arguments."
    ]
  ],
  "syntax": "key element ...",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Inserts specified values at the tail of the list stored at `key`, only if `key`
already exists and holds a list.
In contrary to [RPUSH](/commands/rpush), no operation will be performed when `key` does not yet
exist.

@examples

```cli
RPUSH mylist "Hello"
RPUSHX mylist "World"
RPUSHX myotherlist "World"
LRANGE mylist 0 -1
LRANGE myotherlist 0 -1
```

