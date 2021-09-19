{
  "title": "COPY",
  "summary": "Copy a key",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) worst case for collections, where N is the number of nested items. O(1) for string values.",
  "since": "6.2.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if `source` was copied.\n* `0` if `source` was not copied.",
  "syntax": "source destination [DB destination-db] [REPLACE]",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

This command copies the value stored at the `source` key to the `destination`
key.

By default, the `destination` key is created in the logical database used by the
connection. The `DB` option allows specifying an alternative logical database
index for the destination key.

The command returns an error when the `destination` key already exists. The
`REPLACE` option removes the `destination` key before copying the value to it.

@examples

```
SET dolly "sheep"
COPY dolly clone
GET clone
```
