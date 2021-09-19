{
  "title": "TIME",
  "summary": "Return the current server time",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.6.0",
  "return_summary": "@array-reply, specifically:\n\nA multi bulk reply containing two elements:\n\n* unix time in seconds.\n* microseconds.",
  "syntax": "",
  "acl_categories": [
    "slow"
  ]
}

The [TIME](/commands/time) command returns the current server time as a two items lists: a Unix
timestamp and the amount of microseconds already elapsed in the current second.
Basically the interface is very similar to the one of the `gettimeofday` system
call.

@examples

```cli
TIME
TIME
```

