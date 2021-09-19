{
  "title": "RANDOMKEY",
  "summary": "Return a random key from the keyspace",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@bulk-string-reply: the random key, or `nil` when the database is empty.",
  "syntax": "",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Return a random key from the currently selected database.

