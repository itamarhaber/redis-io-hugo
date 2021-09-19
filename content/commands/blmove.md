{
  "title": "BLMOVE",
  "summary": "Pop an element from a list, push it to another list and return it; or block until one is available",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.2.0",
  "return_summary": "@bulk-string-reply: the element being popped from `source` and pushed to `destination`.\nIf `timeout` is reached, a @nil-reply is returned.",
  "deprecated": true,
  "syntax": "source destination LEFT|RIGHT LEFT|RIGHT timeout",
  "acl_categories": [
    "list",
    "blocking",
    "write",
    "slow"
  ]
}

[BLMOVE](/commands/blmove) is the blocking variant of [LMOVE](/commands/lmove).
When `source` contains elements, this command behaves exactly like [LMOVE](/commands/lmove).
When used inside a [MULTI](/commands/multi)/[EXEC](/commands/exec) block, this command behaves exactly like [LMOVE](/commands/lmove).
When `source` is empty, Redis will block the connection until another client
pushes to it or until `timeout` (a double value specifying the maximum number of seconds to block) is reached.
A `timeout` of zero can be used to block indefinitely.

This command comes in place of the now deprecated [BRPOPLPUSH](/commands/brpoplpush). Doing
`BLMOVE RIGHT LEFT` is equivalent.

See [LMOVE](/commands/lmove) for more information.

## Pattern: Reliable queue

Please see the pattern description in the [LMOVE](/commands/lmove) documentation.

## Pattern: Circular list

Please see the pattern description in the [LMOVE](/commands/lmove) documentation.

