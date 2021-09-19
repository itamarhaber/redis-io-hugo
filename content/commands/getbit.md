{
  "title": "GETBIT",
  "summary": "Returns the bit value at offset in the string value stored at key",
  "group": "bitmap",
  "tags": [
    "Command",
    "Bitmap"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.2.0",
  "return_summary": "@integer-reply: the bit value stored at _offset_.",
  "syntax": "key offset",
  "acl_categories": [
    "bitmap",
    "slow"
  ]
}

Returns the bit value at _offset_ in the string value stored at _key_.

When _offset_ is beyond the string length, the string is assumed to be a
contiguous space with 0 bits.
When _key_ does not exist it is assumed to be an empty string, so _offset_ is
always out of range and the value is also assumed to be a contiguous space with
0 bits.

@examples

```cli
SETBIT mykey 7 1
GETBIT mykey 0
GETBIT mykey 7
GETBIT mykey 100
```

