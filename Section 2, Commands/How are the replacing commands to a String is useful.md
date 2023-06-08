

# Real life scenario 

a furniture store has a huge DB and it is slow

```
LIST of Items
| Id  | type | color | Material |
| 1   | couch | red   | leather |
| 2   | table | brown | wood  |
| 3   | chair | green | plastic |
and thousands more.
```
**My job** : make it faster using Redis

-------------
How users mostly interact with DB:
1) Fetch one to three properties of an item
2) Update one to three properties of an item
3) Fetch all properties of an item
4) Create Several items
-------------
# Solution:
## Step 1: gather all possible choices:
colors:
1. red
2. blue
3. green
4. orange
types:
1. couch
2. chair
3. table
materials:
1. leather
2. wood
3. plastic

## Step 2: Encode them:
give each item a single character. e.g.
**colors**
1. r -> red
2. b -> blue
3. g -> green
4. o -> orange
**types:**
1. c -> couch
2. f -> chair
3. t -> table
materials:
1. l -> leather
2. w -> wood
3. p -> plastic

```
Before:
LIST of Items
| Id  | type | color | Material |
| 1   | couch | red   | leather |
| 2   | table | brown | wood  |
| 3   | chair | green | plastic |
```
```
After: Encoded table
LIST of Items
| Id  | type | color | Material |
| 1   | c   | r   | l   |
| 2   | t   | b   | w   |
| 3   | f   | g   | p   |
```

## Step 3, Store them to Redis

using the encoded table above:
in Redis: 
```
item:1 --> crl
item:2 --> tbw
item:3 --> fgp
etc..
```
-----
# So now, back to the users' interaction with DB
1. Fetch one to three properties of an item
```
GETRANGE item:1 0 2
```
1) Update one to three properties of an item
```
SETRANGE item:1 0 cbp
```
3) Fetch all properties of an item
```
MGET item:1 item:2 item:3
```
5) Create Several items
```
MSET item:1 fbl item:2 crl
```
