{
  "title": "KEYS",
  "summary": "Find all keys matching the given pattern",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the number of keys in the database, under the assumption that the key names in the database and the given pattern have limited length.",
  "since": "1.0.0",
  "return_summary": "@array-reply: list of keys matching `pattern`.",
  "syntax": "undefined pattern",
  "acl_categories": [
    "keyspace",
    "dangerous",
    "slow"
  ]
}

Returns all keys matching `pattern`.

While the time complexity for this operation is O(N), the constant times are
fairly low.
For example, Redis running on an entry level laptop can scan a 1 million key
database in 40 milliseconds.

**Warning**: consider [KEYS](/commands/keys) as a command that should only be used in production
environments with extreme care.
It may ruin performance when it is executed against large databases.
This command is intended for debugging and special operations, such as changing
your keyspace layout.
Don't use [KEYS](/commands/keys) in your regular application code.
If you're looking for a way to find keys in a subset of your keyspace, consider
using [SCAN](/commands/scan) or [sets][tdts].

[tdts]: /topics/data-types#sets

Supported glob-style patterns:

* `h?llo` matches `hello`, `hallo` and `hxllo`
* `h*llo` matches `hllo` and `heeeello`
* `h[ae]llo` matches `hello` and `hallo,` but not `hillo`
* `h[^e]llo` matches `hallo`, `hbllo`, ... but not `hello`
* `h[a-b]llo` matches `hallo` and `hbllo`

Use `\` to escape special characters if you want to match them verbatim.

@examples

```cli
MSET firstname Jack lastname Stuntman age 35
KEYS *name*
KEYS a??
KEYS *
```

