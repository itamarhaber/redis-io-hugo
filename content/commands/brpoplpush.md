{
  "title": "BRPOPLPUSH",
  "summary": "Pop an element from a list, push it to another list and return it; or block until one is available",
  "group": "list",
  "tags": [
    "Command",
    "List"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.2.0",
  "return_summary": "@bulk-string-reply: the element being popped from `source` and pushed to `destination`.\nIf `timeout` is reached, a @nil-reply is returned.",
  "history": [
    [
      "6.0",
      "`timeout` is interpreted as a double instead of an integer."
    ]
  ],
  "deprecated": true,
  "syntax": "source destination timeout",
  "acl_categories": [
    "list",
    "blocking",
    "write",
    "slow"
  ]
}

[BRPOPLPUSH](/commands/brpoplpush) is the blocking variant of [RPOPLPUSH](/commands/rpoplpush).
When `source` contains elements, this command behaves exactly like [RPOPLPUSH](/commands/rpoplpush).
When used inside a [MULTI](/commands/multi)/[EXEC](/commands/exec) block, this command behaves exactly like [RPOPLPUSH](/commands/rpoplpush).
When `source` is empty, Redis will block the connection until another client
pushes to it or until `timeout` is reached.
A `timeout` of zero can be used to block indefinitely.

As per Redis 6.2.0, BRPOPLPUSH is considered deprecated. Please prefer [BLMOVE](/commands/blmove) in
new code.

See [RPOPLPUSH](/commands/rpoplpush) for more information.

## Pattern: Reliable queue

Please see the pattern description in the [RPOPLPUSH](/commands/rpoplpush) documentation.

## Pattern: Circular list

Please see the pattern description in the [RPOPLPUSH](/commands/rpoplpush) documentation.

