[LLEN](#help) returns the current length of the list.

> [LLEN friends](#run) => 3

The command [LPOP](#help) removes the first element from the list and returns it.

> [LPOP friends](#run) => "Sam"

The command [RPOP](#help) removes the last element from the list and returns it.

> [RPOP friends](#run) => "Bob"

Note that the list now only has one element:

> [LLEN friends](#run) => 1

> [LRANGE friends 0 -1](#run) => ["Tom"]

