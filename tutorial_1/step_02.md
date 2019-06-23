Other common operations provided by key-value stores are [DEL](#help) to delete a given
key and associated value, SET-if-not-exists (called [SETNX](#help) on Redis) that sets a
key only if it does not already exist, and [INCR](#help) to atomically increment a
number stored at a given key:

[SET connections 10](#run)

[INCR connections](#run) => 11

[INCR connections](#run) => 12

[DEL connections](#run)

[INCR connections<](#run) => 1
