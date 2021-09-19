{
  "title": "SCRIPT FLUSH",
  "summary": "Remove all the scripts from the script cache.",
  "group": "scripting",
  "tags": [
    "Command",
    "Scripting"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) with N being the number of scripts in cache",
  "since": "2.6.0",
  "return_summary": "@simple-string-reply",
  "history": [
    [
      "6.2.0",
      "Added the `ASYNC` and `!SYNC` flushing mode modifiers, as well as the  **lazyfree-lazy-user-flush** configuration directive."
    ]
  ],
  "syntax": "[ASYNC|SYNC]",
  "acl_categories": [
    "scripting",
    "slow"
  ]
}

Flush the Lua scripts cache.

Please refer to the [EVAL](/commands/eval) documentation for detailed information about Redis Lua scripting.

By default, [SCRIPT FLUSH](/commands/script-flush) will synchronously flush the cache.
Starting with Redis 6.2, setting the **lazyfree-lazy-user-flush** configuration directive to "yes" changes the default flush mode to asynchronous.

It is possible to use one of the following modifiers to dictate the flushing mode explicitly:

* `ASYNC`: flushes the cache asynchronously
* `SYNC`: flushes the cache synchronously

