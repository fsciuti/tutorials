Welcome to **Try Redis**, a demonstration of the
**Redis** database!

Please type [TUTORIAL](#run) to begin a brief tutorial, [HELP](#run) to see a list of supported
commands, or any valid Redis command to play with the database.

---
Redis is what is called a key-value store, often referred to as a NoSQL
database. The essence of a key-value store is the ability to store some data,
called a value, inside a key. This data can later be retrieved only if we know
the exact key used to store it. We can use the command [SET](#help) to store the value
"fido" at key "server:name":

> [SET server:name 'fido'](#run)

Redis will store our data permanently, so we can later ask "What is the value
stored at key server:name?" and Redis will reply with "fido":

> [GET server:name](#run) => "fido"

---
Other common operations provided by key-value stores are [DEL](#help) to delete a given
key and associated value, SET-if-not-exists (called [SETNX](#help) on Redis) that sets a
key only if it does not already exist, and [INCR](#help) to atomically increment a
number stored at a given key:

> [SET connections 10](#run)

> [INCR connections](#run) => 11

> [INCR connections](#run) => 12

> [DEL connections](#run)

> [INCR connections<](#run) => 1

---
There is something special about [INCR](#help).  Why do we provide such an operation if
we can do it ourself with a bit of code? After all it is as simple as:

    x = GET count
    x = x + 1
    SET count x

The problem is that doing the increment in this way will only work as long as
there is a single client using the key. See what happens if two clients are
accessing this key at the same time:

1. Client A reads *count* as 10.
2. Client B reads *count* as 10.
3. Client A increments 10 and sets *count* to 11.
4. Client B increments 10 and sets *count* to 11.

We wanted the value to be 12, but instead it is 11! This is because
incrementing the value in this way is not an atomic operation.  Calling the
[INCR](#help) command in Redis will prevent this from happening, because it *is* an
atomic operation. Redis provides many of these atomic operations on different
types of data.

---
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

---
Redis also supports several more complex data structures. The first one we'll
look at is a list.  A list is a series of ordered values.  Some of the
important commands for interacting with lists are [RPUSH](#help), [LPUSH](#help), [LLEN](#help),
[LRANGE](#help), [LPOP](#help), and [RPOP](#help).  You can immediately begin working with a key as
a list, as long as it doesn't already exist as a different type.

> [RPUSH](#help) puts the new value at the end of the list.

> [RPUSH friends "Tom"](#run)

> [RPUSH friends "Bob"](#run)

> [LPUSH](#help) puts the new value at the start of the list.

> [LPUSH friends "Sam"](#run)

[LRANGE](#help) gives a subset of the list. It takes the index of the first element
you want to retrieve as its first parameter and the index of the last element
you want to retrieve as its second parameter. A value of -1 for the second
parameter means to retrieve all elements in the list.

> [LRANGE friends 0 -1](#run) => ["Sam","Tom","Bob"]

> [LRANGE friends 0 1](#run) => ["Sam","Tom"]

> [LRANGE friends 1 2](#run) => ["Tom","Bob"]
