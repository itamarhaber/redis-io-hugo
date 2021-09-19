{
  "title": "LREM",
  "summary": "Remove elements from a list",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+M) where N is the length of the list and M is the number of elements removed.",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the number of removed elements.",
  "syntax": "key count element",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Removes the first `count` occurrences of elements equal to `element` from the list
stored at `key`.
The `count` argument influences the operation in the following ways:

* `count > 0`: Remove elements equal to `element` moving from head to tail.
* `count < 0`: Remove elements equal to `element` moving from tail to head.
* `count = 0`: Remove all elements equal to `element`.

For example, `LREM list -2 "hello"` will remove the last two occurrences of
`"hello"` in the list stored at `list`.

Note that non-existing keys are treated like empty lists, so when `key` does not
exist, the command will always return `0`.

@examples

```cli
RPUSH mylist "hello"
RPUSH mylist "hello"
RPUSH mylist "foo"
RPUSH mylist "hello"
LREM mylist -2 "hello"
LRANGE mylist 0 -1
```

