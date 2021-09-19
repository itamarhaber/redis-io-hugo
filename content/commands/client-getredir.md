{
  "title": "CLIENT GETREDIR",
  "summary": "Get tracking notifications redirection client ID if any",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.0.0",
  "return_summary": "@integer-reply: the ID of the client we are redirecting the notifications to. The command returns `-1` if client tracking is not enabled, or `0` if client tracking is enabled but we are not redirecting the notifications to any client.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

This command returns the client ID we are redirecting our
[tracking](/topics/client-side-caching) notifications to. We set a client
to redirect to when using [CLIENT TRACKING](/commands/client-tracking) to enable tracking. However in
order to avoid forcing client libraries implementations to remember the
ID notifications are redirected to, this command exists in order to improve
introspection and allow clients to check later if redirection is active
and towards which client ID.

