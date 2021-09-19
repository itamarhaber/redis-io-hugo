{
  "title": "LPOP",
  "summary": "Remove and get the first elements in a list",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of elements returned",
  "since": "1.0.0",
  "return_summary": "When called without the `count` argument:\n\n@bulk-string-reply: the value of the first element, or `nil` when `key` does not exist.\n\nWhen called with the `count` argument:\n\n@array-reply: list of popped elements, or `nil` when `key` does not exist.",
  "history": [
    [
      "6.2",
      "Added the `count` argument."
    ]
  ],
  "syntax": "key [count]",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Removes and returns the first elements of the list stored at `key`.

By default, the command pops a single element from the beginning of the list.
When provided with the optional `count` argument, the reply will consist of up
to `count` elements, depending on the list's length.

@examples

```cli
RPUSH mylist "one" "two" "three" "four" "five"
LPOP mylist
LPOP mylist 2
LRANGE mylist 0 -1
```

