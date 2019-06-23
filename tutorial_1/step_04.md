Redis can be told that a key should only exist for a certain length of time.
This is accomplished with the [EXPIRE](#help) and [TTL](#help) commands.

> [SET resource:lock "Redis Demo"</a](#run)

> [EXPIRE resource:lock 120](#run)


This causes the key *resource:lock* to be deleted in 120 seconds. You can test
how long a key will exist for with the [TTL](#help) command. It returns the number of
seconds until it will be deleted.

> [TTL resource:lock](#run) => 113

> [TTL count](#run) => -1


The *-1* for the [TTL](#help) of the key *count* means that it will never expire. Note
that if you [SET](#help) a key, its [TTL](#help) will reset.

> [SET resource:lock "Redis Demo 1"](#run)

> [EXPIRE resource:lock 120](#run)

> [TTL resource:lock](#run) => 119

> [SET resource:lock "Redis Demo 2"](#run)

> [TTL resource:lock](#run) => -1

