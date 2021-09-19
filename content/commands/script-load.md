{
  "title": "SCRIPT LOAD",
  "summary": "Load the specified Lua script into the script cache.",
  "group": "scripting",
  "tags": [
    "Command",
    "Scripting"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the length in bytes of the script body.",
  "since": "2.6.0",
  "return_summary": "@bulk-string-reply This command returns the SHA1 digest of the script added into the\nscript cache.",
  "syntax": "script",
  "acl_categories": [
    "scripting",
    "slow"
  ]
}

Load a script into the scripts cache, without executing it.
After the specified command is loaded into the script cache it will be callable
using [EVALSHA](/commands/evalsha) with the correct SHA1 digest of the script, exactly like after
the first successful invocation of [EVAL](/commands/eval).

The script is guaranteed to stay in the script cache forever (unless `SCRIPT
FLUSH` is called).

The command works in the same way even if the script was already present in the
script cache.

Please refer to the [EVAL](/commands/eval) documentation for detailed information about Redis
Lua scripting.

