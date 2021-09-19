{
  "title": "EVALSHA",
  "summary": "Execute a Lua script server side",
  "group": "scripting",
  "tags": [
    "Command",
    "Scripting"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "Depends on the script that is executed.",
  "since": "2.6.0",
  "return_summary": "<summary>",
  "syntax": "sha1 numkeys [key ...] [arg ...]",
  "acl_categories": [
    "scripting",
    "slow"
  ]
}

Evaluates a script cached on the server side by its SHA1 digest.
Scripts are cached on the server side using the [SCRIPT LOAD](/commands/script-load) command.
The command is otherwise identical to [EVAL](/commands/eval).

