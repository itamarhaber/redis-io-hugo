{
  "title": "SADD",
  "summary": "Add one or more members to a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each element added, so O(N) to add N elements when the command is called with multiple arguments.",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the number of elements that were added to the set, not including\nall the elements already present in the set.",
  "history": [
    [
      "2.4",
      "Accepts multiple `member` arguments."
    ]
  ],
  "syntax": "key member ...",
  "acl_categories": [
    "set",
    "write",
    "slow"
  ]
}

Add the specified members to the set stored at `key`.
Specified members that are already a member of this set are ignored.
If `key` does not exist, a new set is created before adding the specified
members.

An error is returned when the value stored at `key` is not a set.

@examples

```cli
SADD myset "Hello"
SADD myset "World"
SADD myset "World"
SMEMBERS myset
```

