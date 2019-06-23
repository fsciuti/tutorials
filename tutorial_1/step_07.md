The next data structure that we'll look at is a set. A set is similar to a
list, except it does not have a specific order and each element may only appear
once. Some of the important commands in working with sets are [SADD](#help), [SREM](#help),
[SISMEMBER](#help), [SMEMBERS](#help) and [SUNION](#help).

The command [SADD](#help) adds the given value to the set.
> [SADD superpowers "flight"](#run)

> [SADD superpowers "x-ray vision"](#run)

> [SADD superpowers "reflexes"](#run)

The command [SREM](#help) removes the given value from the set.

> [SREM superpowers "reflexes"](#run)
