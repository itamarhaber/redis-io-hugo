{
  "title": "ZSCAN",
  "summary": "Incrementally iterate sorted sets elements and associated scores",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for every call. O(N) for a complete iteration, including enough command calls for the cursor to return back to 0. N is the number of elements inside the collection..",
  "since": "2.8.0",
  "return_summary": "<summary>",
  "syntax": "key cursor [MATCH pattern] [COUNT count]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

See [SCAN](/commands/scan) for [ZSCAN](/commands/zscan) documentation.

