Move `key` from the currently selected database (see [SELECT](/commands/select)) to the specified
destination database.
When `key` already exists in the destination database, or it does not exist in
the source database, it does nothing.
It is possible to use [MOVE](/commands/move) as a locking primitive because of this.

