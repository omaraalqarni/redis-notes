#redis #RedisSetters #redisCommands

## Objectives:
	- GETSET
	- DEL
	- STRLEN
	- SET
	- SETNX
	- SETEX
	- MSET
	- MSETNX
	- APPEND
	- SETRANGE


## DEL
- To delete the key. Works on any data type. e.g:
```
DEL color
```


## SET
Contains of:
1. Key: name to define the value
2. value: value duh
3. Expiring options:
	1. EX: Delete after x seconds ```SET Message 'hello' EX 2 ```
	2. PX :  Delete after x microseconds ```SET Message 'hello' PX 2 ```
	3. EXAT | PXAT: using date-time in the future
	5. KEEPTTL
4. NX | XX
	1. **NX:** ONLY RUN THE SET IF THE KEY **DOES NOT EXIST**
	2. **XX**: ONLY RUN SET IF THE KEY **ALREADY EXIST**



## SET | SETEX | SETNX: They kinda do the same thing
- **SETEX:** is SET + EX, provides to SET and give an expiry seconds limit
``` 
SETEX color 3 'blue'
```
- **SETNX:** is SET + NX , provides to SET only if the **key does not exist**
``` 
SETNX color 'blue'
```

## MSET | MSETNX: They also kinda close to each other
- **MSET:**  multiple SET. e.g: 
``` 
MSET key1 "Hello" key2 "World" 
```
- **MSETNX:** multiple SET that is also **NX**. e.g. 
```
MSETNX key1 "Hello" key2 "there" 1 
```


## SETRANGE
updates a portion of an existing String. e.g:
```
SET key1 "Hello World"
SETRANGE key1 6 "Redis"
RESULT:
"Hello Redis"
```