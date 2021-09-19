{
  "title": "MIGRATE",
  "summary": "Atomically transfer a key from a Redis instance to another one.",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "This command actually executes a DUMP+DEL in the source instance, and a RESTORE in the target instance. See the pages of these commands for time complexity. Also an O(N) data transfer between the two instances is performed.",
  "since": "2.6.0",
  "return_summary": "@simple-string-reply: The command returns OK on success, or `NOKEY` if no keys were\nfound in the source instance.",
  "history": [
    [
      "3.0.0",
      "Added the `COPY` and `REPLACE` options."
    ],
    [
      "3.0.6",
      "Added the `KEYS` option."
    ],
    [
      "4.0.7",
      "Added the `AUTH` option."
    ],
    [
      "6.0.0",
      "Added the `AUTH2` option."
    ]
  ],
  "syntax": "host port key|\"\" destination-db timeout [COPY] [REPLACE] [AUTH password] [AUTH2 username password] [KEYS key]",
  "acl_categories": [
    "keyspace",
    "dangerous",
    "write",
    "slow"
  ]
}

Atomically transfer a key from a source Redis instance to a destination Redis
instance.
On success the key is deleted from the original instance and is guaranteed to
exist in the target instance.

The command is atomic and blocks the two instances for the time required to
transfer the key, at any given time the key will appear to exist in a given
instance or in the other instance, unless a timeout error occurs. In 3.2 and
above, multiple keys can be pipelined in a single call to [MIGRATE](/commands/migrate) by passing
the empty string ("") as key and adding the [KEYS](/commands/keys) clause.

The command internally uses [DUMP](/commands/dump) to generate the serialized version of the key
value, and [RESTORE](/commands/restore) in order to synthesize the key in the target instance.
The source instance acts as a client for the target instance.
If the target instance returns OK to the [RESTORE](/commands/restore) command, the source instance
deletes the key using [DEL](/commands/del).

The timeout specifies the maximum idle time in any moment of the communication
with the destination instance in milliseconds.
This means that the operation does not need to be completed within the specified
amount of milliseconds, but that the transfer should make progresses without
blocking for more than the specified amount of milliseconds.

[MIGRATE](/commands/migrate) needs to perform I/O operations and to honor the specified timeout.
When there is an I/O error during the transfer or if the timeout is reached the
operation is aborted and the special error - `IOERR` returned.
When this happens the following two cases are possible:

* The key may be on both the instances.
* The key may be only in the source instance.

It is not possible for the key to get lost in the event of a timeout, but the
client calling [MIGRATE](/commands/migrate), in the event of a timeout error, should check if the
key is _also_ present in the target instance and act accordingly.

When any other error is returned (starting with `ERR`) [MIGRATE](/commands/migrate) guarantees that
the key is still only present in the originating instance (unless a key with the
same name was also _already_ present on the target instance).

If there are no keys to migrate in the source instance `NOKEY` is returned.
Because missing keys are possible in normal conditions, from expiry for example,
`NOKEY` isn't an error. 

## Migrating multiple keys with a single command call

Starting with Redis 3.0.6 [MIGRATE](/commands/migrate) supports a new bulk-migration mode that
uses pipelining in order to migrate multiple keys between instances without
incurring in the round trip time latency and other overheads that there are
when moving each key with a single [MIGRATE](/commands/migrate) call.

In order to enable this form, the [KEYS](/commands/keys) option is used, and the normal *key*
argument is set to an empty string. The actual key names will be provided
after the [KEYS](/commands/keys) argument itself, like in the following example:

    MIGRATE 192.168.1.34 6379 "" 0 5000 KEYS key1 key2 key3

When this form is used the `NOKEY` status code is only returned when none
of the keys is present in the instance, otherwise the command is executed, even if
just a single key exists.

## Options

* [COPY](/commands/copy) -- Do not remove the key from the local instance.
* `REPLACE` -- Replace existing key on the remote instance.
* [KEYS](/commands/keys) -- If the key argument is an empty string, the command will instead migrate all the keys that follow the [KEYS](/commands/keys) option (see the above section for more info).
* [AUTH](/commands/auth) -- Authenticate with the given password to the remote instance.
* `AUTH2` -- Authenticate with the given username and password pair (Redis 6 or greater ACL auth style).
