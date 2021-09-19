{
  "title": "XLEN",
  "summary": "Return the number of entries in a stream",
  "group": "stream",
  "tags": [
    "Command",
    "Stream"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "5.0.0",
  "return_summary": "@integer-reply: the number of entries of the stream at `key`.",
  "syntax": "key",
  "acl_categories": [
    "stream",
    "slow"
  ]
}

Returns the number of entries inside a stream. If the specified key does not
exist the command returns zero, as if the stream was empty.
However note that unlike other Redis types, zero-length streams are
possible, so you should call [TYPE](/commands/type) or [EXISTS](/commands/exists) in order to check if
a key exists or not.

Streams are not auto-deleted once they have no entries inside (for instance
after an [XDEL](/commands/xdel) call), because the stream may have consumer groups
associated with it.

@examples

```cli
XADD mystream * item 1
XADD mystream * item 2
XADD mystream * item 3
XLEN mystream
```

