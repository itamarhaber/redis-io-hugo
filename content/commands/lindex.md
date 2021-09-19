{
  "title": "LINDEX",
  "summary": "Get an element from a list by its index",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of elements to traverse to get to the element at index. This makes asking for the first or the last element of the list O(1).",
  "since": "1.0.0",
  "return_summary": "@bulk-string-reply: the requested element, or `nil` when `index` is out of range.",
  "syntax": "key index",
  "acl_categories": [
    "list",
    "slow"
  ]
}

Returns the element at index `index` in the list stored at `key`.
The index is zero-based, so `0` means the first element, `1` the second element
and so on.
Negative indices can be used to designate elements starting at the tail of the
list.
Here, `-1` means the last element, `-2` means the penultimate and so forth.

When the value at `key` is not a list, an error is returned.

@examples

```cli
LPUSH mylist "World"
LPUSH mylist "Hello"
LINDEX mylist 0
LINDEX mylist -1
LINDEX mylist 3
```

