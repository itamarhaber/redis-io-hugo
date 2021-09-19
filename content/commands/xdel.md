{
  "title": "XDEL",
  "summary": "Removes the specified entries from the stream. Returns the number of items actually deleted, that may be different from the number of IDs passed in case certain IDs do not exist.",
  "group": "stream",
  "tags": [
    "Command",
    "Stream"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each single item to delete in the stream, regardless of the stream size.",
  "since": "5.0.0",
  "return_summary": "@integer-reply: the number of entries actually deleted.",
  "syntax": "key ID ...",
  "acl_categories": [
    "stream",
    "write",
    "slow"
  ]
}

Removes the specified entries from a stream, and returns the number of entries
deleted, that may be different from the number of IDs passed to the command in
case certain IDs do not exist.

Normally you may think at a Redis stream as an append-only data structure,
however Redis streams are represented in memory, so we are able to also
delete entries. This may be useful, for instance, in order to comply with
certain privacy policies.

# Understanding the low level details of entries deletion

Redis streams are represented in a way that makes them memory efficient:
a radix tree is used in order to index macro-nodes that pack linearly tens
of stream entries. Normally what happens when you delete an entry from a stream
is that the entry is not *really* evicted, it just gets marked as deleted.

Eventually if all the entries in a macro-node are marked as deleted, the whole
node is destroyed and the memory reclaimed. This means that if you delete
a large amount of entries from a stream, for instance more than 50% of the
entries appended to the stream, the memory usage per entry may increment, since
what happens is that the stream will start to be fragmented. However the stream
performances will remain the same.

In future versions of Redis it is possible that we'll trigger a node garbage
collection in case a given macro-node reaches a given amount of deleted
entries. Currently with the usage we anticipate for this data structure, it is
not a good idea to add such complexity.

@examples

```
> XADD mystream * a 1
1538561698944-0
> XADD mystream * b 2
1538561700640-0
> XADD mystream * c 3
1538561701744-0
> XDEL mystream 1538561700640-0
(integer) 1
127.0.0.1:6379> XRANGE mystream - +
1) 1) 1538561698944-0
   2) 1) "a"
      2) "1"
2) 1) 1538561701744-0
   2) 1) "c"
      2) "3"
```

