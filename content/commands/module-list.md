{
  "title": "MODULE LIST",
  "summary": "List all modules loaded by the server",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of loaded modules.",
  "since": "4.0.0",
  "return_summary": "@array-reply: list of loaded modules. Each element in the list represents a\nmodule, and is in itself a list of property names and their values. The\nfollowing properties is reported for each loaded module:\n\n*   `name`: Name of the module\n*   `ver`: Version of the module",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Returns information about the modules loaded to the server.

