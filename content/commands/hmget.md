Returns the values associated with the specified `fields` in the hash stored at
`key`.

For every `field` that does not exist in the hash, a `nil` value is returned.
Because non-existing keys are treated as empty hashes, running [HMGET](/commands/hmget) against
a non-existing `key` will return a list of `nil` values.

