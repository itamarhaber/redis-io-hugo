{
  "title": "SPOP",
  "summary": "Remove and return one or multiple random members from a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "Without the count argument O(1), otherwise O(N) where N is the value of the passed count.",
  "since": "1.0.0",
  "return_summary": "When called without the `count` argument:\n\n@bulk-string-reply: the removed member, or `nil` when `key` does not exist.\n\nWhen called with the `count` argument:\n\n@array-reply: the removed members, or an empty array when `key` does not exist.",
  "history": [
    [
      "3.2",
      "Added the `count` argument."
    ]
  ],
  "syntax": "key [count]",
  "acl_categories": [
    "set",
    "write",
    "slow"
  ]
}

Removes and returns one or more random members from the set value store at `key`.

This operation is similar to [SRANDMEMBER](/commands/srandmember), that returns one or more random elements from a set but does not remove it.

By default, the command pops a single member from the set. When provided with
the optional `count` argument, the reply will consist of up to `count` members,
depending on the set's cardinality.

@examples

```cli
SADD myset "one"
SADD myset "two"
SADD myset "three"
SPOP myset
SMEMBERS myset
SADD myset "four"
SADD myset "five"
SPOP myset 3
SMEMBERS myset
```
## Distribution of returned elements

Note that this command is not suitable when you need a guaranteed uniform distribution of the returned elements. For more information about the algorithms used for [SPOP](/commands/spop), look up both the Knuth sampling and Floyd sampling algorithms.

