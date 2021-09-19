{
  "title": "SCRIPT EXISTS",
  "summary": "Check existence of scripts in the script cache.",
  "group": "scripting",
  "tags": [
    "Command",
    "Scripting"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the number of scripts to check (so checking a single script is an O(1) operation).",
  "since": "2.6.0",
  "return_summary": "@array-reply The command returns an array of integers that correspond to\nthe specified SHA1 digest arguments.\nFor every corresponding SHA1 digest of a script that actually exists in the\nscript cache, an 1 is returned, otherwise 0 is returned.",
  "syntax": "sha1 ...",
  "acl_categories": [
    "scripting",
    "slow"
  ]
}

Returns information about the existence of the scripts in the script cache.

This command accepts one or more SHA1 digests and returns a list of ones or
zeros to signal if the scripts are already defined or not inside the script
cache.
This can be useful before a pipelining operation to ensure that scripts are
loaded (and if not, to load them using [SCRIPT LOAD](/commands/script-load)) so that the pipelining
operation can be performed solely using [EVALSHA](/commands/evalsha) instead of [EVAL](/commands/eval) to save
bandwidth.

Please refer to the [EVAL](/commands/eval) documentation for detailed information about Redis
Lua scripting.

