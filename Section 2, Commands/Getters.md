#redis #RedisGetters #redisCommands


## Objectives: 
	- MGET
	- GET
	- GETDEL
	- GETEX
	- SUBSTR
	- GETRANGE
	- LCS



## MGET | GET | GETEX | GETDEL" Kinda do the Same Thing

- MGET:  Multiple GET. For every key that does not hold a string value or does not exist, the special value `nil` is returned. Because of this, the operation never fails.
```
MGET key [key ...]
EX: 
SET key1 "Hello"
SET key2 "World"
MGET key1 key2 nonexisting
Result:
 "Hello"
 "World"
 (nil) 		
```

- GET: gets a plain text or number. e.g:
```
GET Message // GET <name> 
```

- GETEX: get a value and delete it after specified number of seconds. e.g:
```
GETEX color blue 200
```

-  GETDEL: Get the value of `key` and delete the key.  it also deletes the key on success (if and only if the key's value type is a string). e.g:
```
Ex:
SET mykey "Hello"
GETDEL mykey
"Hello" //result
GET mykey
(nil) // result
```


## SUBSTR | GETRANGE | LCS: Not super obvious use cases

-  SUBSTR
- GETRANGE:
	- returns a substring of the String based on the query. e.g:
```
SET mykey "This is a string"
GETRANGE mykey 0 3
RESULT:
"This"
```
-  LCS