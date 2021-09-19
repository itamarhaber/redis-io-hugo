{
  "title": "GEOSEARCHSTORE",
  "summary": "Query a sorted set representing a geospatial index to fetch members inside an area of a box or a circle, and store the result in another key.",
  "group": "geo",
  "tags": [
    "Command",
    "Geo"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+log(M)) where N is the number of elements in the grid-aligned bounding box area around the shape provided as the filter and M is the number of items inside the shape",
  "since": "6.2",
  "return_summary": "@integer-reply: the number of elements in the resulting set.",
  "deprecated": true,
  "syntax": "destination source [FROMMEMBER member] [FROMLONLAT longitude latitude] [BYRADIUS radius m|km|ft|mi] [BYBOX width height m|km|ft|mi] [ASC|DESC] [COUNT count [ANY]] [STOREDIST]",
  "acl_categories": [
    "geo",
    "write",
    "slow"
  ]
}

This command is like [GEOSEARCH](/commands/geosearch), but stores the result in destination key.

This command comes in place of the now deprecated [GEORADIUS](/commands/georadius) and [GEORADIUSBYMEMBER](/commands/georadiusbymember).

By default, it stores the results in the `destination` sorted set with their geospatial information.

When using the `STOREDIST` option, the command stores the items in a sorted set populated with their distance from the center of the circle or box, as a floating-point number, in the same unit specified for that shape.

@examples

```cli
GEOADD Sicily 13.361389 38.115556 "Palermo" 15.087269 37.502669 "Catania"
GEOADD Sicily 12.758489 38.788135 "edge1"   17.241510 38.788135 "edge2" 
GEOSEARCHSTORE key1 Sicily FROMLONLAT 15 37 BYBOX 400 400 km ASC COUNT 3
GEOSEARCH key1 FROMLONLAT 15 37 BYBOX 400 400 km ASC WITHCOORD WITHDIST WITHHASH
GEOSEARCHSTORE key2 Sicily FROMLONLAT 15 37 BYBOX 400 400 km ASC COUNT 3 STOREDIST
ZRANGE key2 0 -1 WITHSCORES
```
