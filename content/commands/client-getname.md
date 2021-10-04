The [CLIENT GETNAME](/commands/client-getname) returns the name of the current connection as set by [CLIENT SETNAME](/commands/client-setname). Since every new connection starts without an associated name, if no name was assigned a null bulk reply is returned.

