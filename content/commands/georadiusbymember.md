{
  "title": "GEORADIUSBYMEMBER",
  "summary": "Query a sorted set representing a geospatial index to fetch members matching a given maximum distance from a member",
  "group": "geo",
  "tags": [
    "Command",
    "Geo"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+log(M)) where N is the number of elements inside the bounding box of the circular area delimited by center and radius and M is the number of items inside the index.",
  "since": "3.2.0",
  "return_summary": "<summary>",
  "deprecated": true,
  "syntax": "key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count [ANY]] [ASC|DESC] [STORE key] [STOREDIST key]",
  "acl_categories": [
    "geo",
    "write",
    "slow"
  ]
}

This command is exactly like [GEORADIUS](/commands/georadius) with the sole difference that instead
of taking, as the center of the area to query, a longitude and latitude value, it takes the name of a member already existing inside the geospatial index represented by the sorted set.

As per Redis 6.2.0, GEORADIUS command family are considered deprecated. Please prefer [GEOSEARCH](/commands/geosearch) and [GEOSEARCHSTORE](/commands/geosearchstore) in new code.

The position of the specified member is used as the center of the query.

Please check the example below and the [GEORADIUS](/commands/georadius) documentation for more information about the command and its options.

Note that `GEORADIUSBYMEMBER_RO` is also available since Redis 3.2.10 and Redis 4.0.0 in order to provide a read-only command that can be used in replicas. See the [GEORADIUS](/commands/georadius) page for more information.

@examples

```cli
GEOADD Sicily 13.583333 37.316667 "Agrigento"
GEOADD Sicily 13.361389 38.115556 "Palermo" 15.087269 37.502669 "Catania"
GEORADIUSBYMEMBER Sicily Agrigento 100 km
```

