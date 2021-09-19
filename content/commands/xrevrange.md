{
  "title": "XREVRANGE",
  "summary": "Return a range of elements in a stream, with IDs matching the specified IDs interval, in reverse order (from greater to smaller IDs) compared to XRANGE",
  "group": "stream",
  "tags": [
    "Command",
    "Stream"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the number of elements returned. If N is constant (e.g. always asking for the first 10 elements with COUNT), you can consider it O(1).",
  "since": "5.0.0",
  "return_summary": "@array-reply, specifically:\n\nThe command returns the entries with IDs matching the specified range,\nfrom the higher ID to the lower ID matching.\nThe returned entries are complete, that means that the ID and all the fields\nthey are composed are returned. Moreover the entries are returned with\ntheir fields and values in the exact same order as `XADD` added them.",
  "syntax": "key end start [COUNT count]",
  "acl_categories": [
    "stream",
    "slow"
  ]
}

This command is exactly like [XRANGE](/commands/xrange), but with the notable difference of
returning the entries in reverse order, and also taking the start-end
range in reverse order: in [XREVRANGE](/commands/xrevrange) you need to state the *end* ID
and later the *start* ID, and the command will produce all the element
between (or exactly like) the two IDs, starting from the *end* side.

So for instance, to get all the elements from the higher ID to the lower
ID one could use:

    XREVRANGE somestream + -

Similarly to get just the last element added into the stream it is
enough to send:

    XREVRANGE somestream + - COUNT 1

@examples

```cli
XADD writers * name Virginia surname Woolf
XADD writers * name Jane surname Austen
XADD writers * name Toni surname Morrison
XADD writers * name Agatha surname Christie
XADD writers * name Ngozi surname Adichie
XLEN writers
XREVRANGE writers + - COUNT 1
```

