{
  "title": "CLIENT TRACKINGINFO",
  "summary": "Return information about server assisted client side caching for the current connection",
  "group": "connection",
  "tags": [
    "Command",
    "Connection"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "6.2.0",
  "return_summary": "@array-reply: a list of tracking information sections and their respective values, specifically:\n\n* **flags**: A list of tracking flags used by the connection. The flags and their meanings are as follows:\n  * `off`: The connection isn't using server assisted client side caching.\n  * `on`: Server assisted client side caching is enabled for the connection.\n  * `bcast`: The client uses broadcasting mode.\n  * `optin`: The client does not cache keys by default.\n  * `optout`: The client caches keys by default.\n  * `caching-yes`: The next command will cache keys (exists only together with `optin`).\n  * `caching-no`: The next command won't cache keys (exists only together with `optout`).\n  * `noloop`: The client isn't notified about keys modified by itself.\n  * `broken_redirect`: The client ID used for redirection isn't valid anymore.\n* **redirect**: The client ID used for notifications redirection, or -1 when none.\n* **prefixes**: A list of key prefixes for which notifications are sent to the client.",
  "syntax": "",
  "acl_categories": [
    "connection",
    "admin",
    "dangerous",
    "slow"
  ]
}

The command returns information about the current client connection's use of the [server assisted client side caching](/topics/client-side-caching) feature.

