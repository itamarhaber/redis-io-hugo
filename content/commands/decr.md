{
  "title": "DECR",
  "summary": "Decrement the integer value of a key by one",
  "group": "string",
  "tags": [
    "Command",
    "String"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the value of `key` after the decrement",
  "syntax": "key",
  "acl_categories": [
    "string",
    "write",
    "slow"
  ]
}

Decrements the number stored at `key` by one.
If the key does not exist, it is set to `0` before performing the operation.
An error is returned if the key contains a value of the wrong type or contains a
string that can not be represented as integer.
This operation is limited to **64 bit signed integers**.

See [INCR](/commands/incr) for extra information on increment/decrement operations.

@examples

```cli
SET mykey "10"
DECR mykey
SET mykey "234293482390480948029348230948"
DECR mykey
```

