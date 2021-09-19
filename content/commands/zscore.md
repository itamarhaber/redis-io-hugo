{
  "title": "ZSCORE",
  "summary": "Get the score associated with the given member in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.2.0",
  "return_summary": "@bulk-string-reply: the score of `member` (a double precision floating point number),\nrepresented as string.",
  "syntax": "key member",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the score of `member` in the sorted set at `key`.

If `member` does not exist in the sorted set, or `key` does not exist, `nil` is
returned.

@examples

```cli
ZADD myzset 1 "one"
ZSCORE myzset "one"
```

