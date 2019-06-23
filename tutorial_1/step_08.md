[SISMEMBER](#help) tests if the given value is in the set.

> [SISMEMBER superpowers "flight"](#run) => true

> [SISMEMBER superpowers "reflexes"](#run) => false

The command [SMEMBERS](#help) returns a list of all the members of this set.

> [SMEMBERS superpowers](#run)> => ["flight","x-ray vision"]


The command [SUNION](#help) combines two or more sets and returns the list of all elements.

> [SADD birdpowers "pecking"](#run)

> [SADD birdpowers "flight"](#run)

> [SUNION superpowers birdpowers](#run) => ["flight","x-ray vision","pecking"]

