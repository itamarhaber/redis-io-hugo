{
  "title": "BITCOUNT",
  "summary": "Count set bits in a string",
  "group": "bitmap",
  "tags": [
    "Command",
    "Bitmap"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N)",
  "since": "2.6.0",
  "return_summary": "@integer-reply\n\nThe number of bits set to 1.",
  "syntax": "key [start end]",
  "acl_categories": [
    "bitmap",
    "slow"
  ]
}

Count the number of set bits (population counting) in a string.

By default all the bytes contained in the string are examined.
It is possible to specify the counting operation only in an interval passing the
additional arguments _start_ and _end_.

Like for the [GETRANGE](/commands/getrange) command start and end can contain negative values in
order to index bytes starting from the end of the string, where -1 is the last
byte, -2 is the penultimate, and so forth.

Non-existent keys are treated as empty strings, so the command will return zero.

@examples

```cli
SET mykey "foobar"
BITCOUNT mykey
BITCOUNT mykey 0 0
BITCOUNT mykey 1 1
```

## Pattern: real-time metrics using bitmaps

Bitmaps are a very space-efficient representation of certain kinds of
information.
One example is a Web application that needs the history of user visits, so that
for instance it is possible to determine what users are good targets of beta
features.

Using the [SETBIT](/commands/setbit) command this is trivial to accomplish, identifying every day
with a small progressive integer.
For instance day 0 is the first day the application was put online, day 1 the
next day, and so forth.

Every time a user performs a page view, the application can register that in
the current day the user visited the web site using the [SETBIT](/commands/setbit) command setting
the bit corresponding to the current day.

Later it will be trivial to know the number of single days the user visited the
web site simply calling the [BITCOUNT](/commands/bitcount) command against the bitmap.

A similar pattern where user IDs are used instead of days is described
in the article called "[Fast easy realtime metrics using Redis
bitmaps][hbgc212fermurb]".

[hbgc212fermurb]: http://blog.getspool.com/2011/11/29/fast-easy-realtime-metrics-using-redis-bitmaps

## Performance considerations

In the above example of counting days, even after 10 years the application is
online we still have just `365*10` bits of data per user, that is just 456 bytes
per user.
With this amount of data [BITCOUNT](/commands/bitcount) is still as fast as any other O(1) Redis
command like [GET](/commands/get) or [INCR](/commands/incr).

When the bitmap is big, there are two alternatives:

* Taking a separated key that is incremented every time the bitmap is modified.
  This can be very efficient and atomic using a small Redis Lua script.
* Running the bitmap incrementally using the [BITCOUNT](/commands/bitcount) _start_ and _end_
  optional parameters, accumulating the results client-side, and optionally
  caching the result into a key.
