{
  "title": "SMOVE",
  "summary": "Move a member from one set to another",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the element is moved.\n* `0` if the element is not a member of `source` and no operation was performed.",
  "syntax": "source destination member",
  "acl_categories": [
    "set",
    "write",
    "slow"
  ]
}

Move `member` from the set at `source` to the set at `destination`.
This operation is atomic.
In every given moment the element will appear to be a member of `source` **or**
`destination` for other clients.

If the source set does not exist or does not contain the specified element, no
operation is performed and `0` is returned.
Otherwise, the element is removed from the source set and added to the
destination set.
When the specified element already exists in the destination set, it is only
removed from the source set.

An error is returned if `source` or `destination` does not hold a set value.

@examples

```cli
SADD myset "one"
SADD myset "two"
SADD myotherset "three"
SMOVE myset myotherset "two"
SMEMBERS myset
SMEMBERS myotherset
```
