Returns the specified range of elements in the sorted set stored at `key`.
The elements are considered to be ordered from the highest to the lowest score.
Descending lexicographical order is used for elements with equal score.

Apart from the reversed ordering, [ZREVRANGE](/commands/zrevrange) is similar to [ZRANGE](/commands/zrange).

As per Redis 6.2.0, this command is considered deprecated. Please prefer using the [ZRANGE](/commands/zrange) command with the `REV` argument in new code.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREVRANGE myzset 0 -1
ZREVRANGE myzset 2 3
ZREVRANGE myzset -2 -1
```

