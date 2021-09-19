{
  "title": "EVALSHA_RO",
  "summary": "Execute a read-only Lua script server side",
  "group": "scripting",
  "tags": [
    "Command",
    "Scripting"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "Depends on the script that is executed.",
  "since": "7.0.0",
  "return_summary": "<summary>",
  "syntax": "sha1 numkeys key ... arg ...",
  "acl_categories": [
    "scripting",
    "slow"
  ]
}

This is a read-only variant of the [EVALSHA](/commands/evalsha) command that isn't allowed to execute commands that modify data.

 Unlike [EVALSHA](/commands/evalsha), scripts executed with this command can always be killed and never affect the replication stream.
 Because it can only read data, this command can always be executed on a master or a replica.

