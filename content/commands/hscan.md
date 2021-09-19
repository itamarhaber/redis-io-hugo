{
  "title": "HSCAN",
  "summary": "Incrementally iterate hash fields and associated values",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for every call. O(N) for a complete iteration, including enough command calls for the cursor to return back to 0. N is the number of elements inside the collection..",
  "since": "2.8.0",
  "return_summary": "<summary>",
  "syntax": "key cursor [MATCH pattern] [COUNT count]",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

See [SCAN](/commands/scan) for [HSCAN](/commands/hscan) documentation.

