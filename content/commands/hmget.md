{
  "title": "HMGET",
  "summary": "Get the values of all the given hash fields",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of fields being requested.",
  "since": "2.0.0",
  "return_summary": "@array-reply: list of values associated with the given fields, in the same\norder as they are requested.\n\n```cli\nHSET myhash field1 \"Hello\"\nHSET myhash field2 \"World\"\nHMGET myhash field1 field2 nofield\n```",
  "syntax": "key field ...",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns the values associated with the specified `fields` in the hash stored at
`key`.

For every `field` that does not exist in the hash, a `nil` value is returned.
Because non-existing keys are treated as empty hashes, running [HMGET](/commands/hmget) against
a non-existing `key` will return a list of `nil` values.

