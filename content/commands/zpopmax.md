{
  "title": "ZPOPMAX",
  "summary": "Remove and return members with the highest scores in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)*M) with N being the number of elements in the sorted set, and M being the number of elements popped.",
  "since": "5.0.0",
  "return_summary": "@array-reply: list of popped elements and scores.",
  "syntax": "key [count]",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Removes and returns up to `count` members with the highest scores in the sorted
set stored at `key`.

When left unspecified, the default value for `count` is 1. Specifying a `count`
value that is higher than the sorted set's cardinality will not produce an
error. When returning multiple elements, the one with the highest score will
be the first, followed by the elements with lower scores.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZPOPMAX myzset
```

