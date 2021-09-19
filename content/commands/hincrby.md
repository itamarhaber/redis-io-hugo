{
  "title": "HINCRBY",
  "summary": "Increment the integer value of a hash field by the given number",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@integer-reply: the value at `field` after the increment operation.",
  "syntax": "key field increment",
  "acl_categories": [
    "hash",
    "write",
    "slow"
  ]
}

Increments the number stored at `field` in the hash stored at `key` by
`increment`.
If `key` does not exist, a new key holding a hash is created.
If `field` does not exist the value is set to `0` before the operation is
performed.

The range of values supported by [HINCRBY](/commands/hincrby) is limited to 64 bit signed integers.

@examples

Since the `increment` argument is signed, both increment and decrement
operations can be performed:

```cli
HSET myhash field 5
HINCRBY myhash field 1
HINCRBY myhash field -1
HINCRBY myhash field -10
```

