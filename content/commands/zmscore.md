{
  "title": "ZMSCORE",
  "summary": "Get the score associated with the given members in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of members being requested.",
  "since": "6.2.0",
  "return_summary": "@array-reply: list of scores or `nil` associated with the specified `member` values (a double precision floating point number),\nrepresented as strings.",
  "syntax": "key member ...",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the scores associated with the specified `members` in the sorted set stored at `key`.

For every `member` that does not exist in the sorted set, a `nil` value is returned.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZMSCORE myzset "one" "two" "nofield"
```

