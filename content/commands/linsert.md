{
  "title": "LINSERT",
  "summary": "Insert an element before or after another element in a list",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of elements to traverse before seeing the value pivot. This means that inserting somewhere on the left end on the list (head) can be considered O(1) and inserting somewhere on the right end (tail) is O(N).",
  "since": "2.2.0",
  "return_summary": "@integer-reply: the length of the list after the insert operation, or `-1` when\nthe value `pivot` was not found.",
  "syntax": "key BEFORE|AFTER pivot element",
  "acl_categories": [
    "list",
    "write",
    "slow"
  ]
}

Inserts `element` in the list stored at `key` either before or after the reference
value `pivot`.

When `key` does not exist, it is considered an empty list and no operation is
performed.

An error is returned when `key` exists but does not hold a list value.

@examples

```cli
RPUSH mylist "Hello"
RPUSH mylist "World"
LINSERT mylist BEFORE "World" "There"
LRANGE mylist 0 -1
```

