{
  "title": "MODULE UNLOAD",
  "summary": "Unload a module",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "4.0.0",
  "return_summary": "@simple-string-reply: `OK` if module was unloaded.",
  "syntax": "name",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Unloads a module.

This command unloads the module specified by `name`. Note that the module's name
is reported by the [MODULE LIST](/commands/module-list) command, and may differ from the dynamic
library's filename.

Known limitations:

*   Modules that register custom data types can not be unloaded.

