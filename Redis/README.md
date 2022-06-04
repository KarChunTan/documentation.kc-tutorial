<div align="center">
  <a href="https://redis.io/">
    <img src="images/redis_logo.svg" alt="Redis Logo" width="200" />
  </a>
  <br />
  <h3 align="center">Redis</h3>
  <p align="center">
    Welcome to my Redis tutorial to jumpstart your projects!
    <br />
    <a href="https://redis.io/docs/">
      <strong>Explore the docs »</strong>
    </a>
    <br />
    <br />
    <a href="https://github.com/KarChunTan/documentation.kc-tutorial/issues">Report Bug</a>
    ·
    <a href="https://github.com/KarChunTan/documentation.kc-tutorial/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
- [What is Redis?](#what-is-redis)
- [Benefits of a Multi-Model DB (Redis)](#benefits-of-a-multi-model-db-redis)
- [How does Redis works support multiple data formats?](#how-does-redis-works-support-multiple-data-formats)
- [Data Persistance & Durability with Redis](#data-persistance--durability-with-redis)
  - [How to keep the data safely persisted?](#how-to-keep-the-data-safely-persisted)
- [How to scale a Redis DB?](#how-to-scale-a-redis-db)
- [Commands Reference](#commands-reference)
  - [Start the Redis server](#start-the-redis-server)
  - [Connect to Redis](#connect-to-redis)
  - [Strings](#strings)
    - [Create a new variable](#create-a-new-variable)
    - [Create multiple key-value pair variables](#create-multiple-key-value-pair-variables)
    - [Create a variable that will be expired in how many seconds](#create-a-variable-that-will-be-expired-in-how-many-seconds)
    - [Create a variable if the variable is not exists](#create-a-variable-if-the-variable-is-not-exists)
    - [Get a variable](#get-a-variable)
    - [Get multiple key-value pair variables](#get-multiple-key-value-pair-variables)
    - [Get the first num characters](#get-the-first-num-characters)
    - [Get length of string](#get-length-of-string)
    - [increment by 1 - incr will always increase by 1](#increment-by-1---incr-will-always-increase-by-1)
    - [increment by number](#increment-by-number)
    - [decrement by 1 - decr will always decrease by 1](#decrement-by-1---decr-will-always-decrease-by-1)
    - [decrement by number](#decrement-by-number)
    - [increment float](#increment-float)
    - [Delete the variable in total seconds](#delete-the-variable-in-total-seconds)
    - [Check the variable left how many seconds to be deleted](#check-the-variable-left-how-many-seconds-to-be-deleted)
  - [List all the variables that had set](#list-all-the-variables-that-had-set)
  - [Delete all variables that had set](#delete-all-variables-that-had-set)
  - [Lists](#lists)
    - [Left Push element to lists (Sounds like Stack Push)](#left-push-element-to-lists-sounds-like-stack-push)
    - [Right Push element to lists (Sounds like Queue Push)](#right-push-element-to-lists-sounds-like-queue-push)
    - [Get the list of data based on range](#get-the-list-of-data-based-on-range)
    - [Get the length of the lists](#get-the-length-of-the-lists)
    - [Left Pop element (Pop the first element)](#left-pop-element-pop-the-first-element)
    - [Right Pop element (Pop the last element)](#right-pop-element-pop-the-last-element)
    - [Change the value of Lists index element](#change-the-value-of-lists-index-element)
    - [Insert the value before/after the element](#insert-the-value-beforeafter-the-element)
    - [Get the value using index](#get-the-value-using-index)
    - [Push to the lists if the lists exists](#push-to-the-lists-if-the-lists-exists)
    - [Sort the data](#sort-the-data)
    - [remove 1 element in the lists if the key exists, else, will be terminated after the timeout](#remove-1-element-in-the-lists-if-the-key-exists-else-will-be-terminated-after-the-timeout)
  - [Sets](#sets)
    - [Add to sets](#add-to-sets)
    - [List all data in sets](#list-all-data-in-sets)
    - [Get the length of the sets](#get-the-length-of-the-sets)
    - [Search data exists in sets](#search-data-exists-in-sets)
    - [Get the differences between multiple sets](#get-the-differences-between-multiple-sets)
    - [Store the differences between multiple sets into new sets](#store-the-differences-between-multiple-sets-into-new-sets)
    - [Get the intersection element between sets](#get-the-intersection-element-between-sets)
    - [Store the intersections between multiple sets into new sets](#store-the-intersections-between-multiple-sets-into-new-sets)
    - [Get the union element between sets](#get-the-union-element-between-sets)
    - [Store the unions between multiple sets into new sets](#store-the-unions-between-multiple-sets-into-new-sets)
  - [Sorted Sets](#sorted-sets)
    - [Add to sorted sets](#add-to-sorted-sets)
    - [List all data in sorted sets](#list-all-data-in-sorted-sets)
    - [Get the length of sorted sets](#get-the-length-of-sorted-sets)
    - [Get the length of sorted sets based on min and max](#get-the-length-of-sorted-sets-based-on-min-and-max)
    - [Remove element from sorted sets](#remove-element-from-sorted-sets)
    - [Reverse the sorted sets](#reverse-the-sorted-sets)
    - [Get the score of the member](#get-the-score-of-the-member)
    - [Reverse the sorted sets based on score](#reverse-the-sorted-sets-based-on-score)
    - [Increase the score value by member](#increase-the-score-value-by-member)
    - [Remove the data by range of score](#remove-the-data-by-range-of-score)
    - [Remove the data by rank](#remove-the-data-by-rank)
  - [HyperLogLog](#hyperloglog)
    - [Add data to hyperloglog](#add-data-to-hyperloglog)
    - [Get the length of hyperloglog](#get-the-length-of-hyperloglog)
    - [Merge multiple hyperloglog to new hyperloglog](#merge-multiple-hyperloglog-to-new-hyperloglog)
  - [Hashes](#hashes)
    - [Add new hastset key-value pair](#add-new-hastset-key-value-pair)
    - [Get all the hash keys from key](#get-all-the-hash-keys-from-key)
    - [Get all the hash values from key](#get-all-the-hash-values-from-key)
    - [Get all hash keys and values from key](#get-all-hash-keys-and-values-from-key)
    - [Check hash keys exists](#check-hash-keys-exists)
    - [Get length of hash](#get-length-of-hash)
    - [Add multiple hashset key-value pairs](#add-multiple-hashset-key-value-pairs)
    - [Get multiple hashset key-value pairs](#get-multiple-hashset-key-value-pairs)
    - [Increment the hash_value by number](#increment-the-hash_value-by-number)
    - [Delete hash_key](#delete-hash_key)
  - [Transactions](#transactions)
  - [PubSub](#pubsub)
    - [Setup subscriber with pattern](#setup-subscriber-with-pattern)
    - [Display all channels without pattern subscribers](#display-all-channels-without-pattern-subscribers)
    - [Get the total of subscribers from that channels](#get-the-total-of-subscribers-from-that-channels)
    - [Get the total of pattern channels](#get-the-total-of-pattern-channels)
  - [Connection & Security](#connection--security)
    - [Switch to different database connection](#switch-to-different-database-connection)
    - [List all the client](#list-all-the-client)
    - [Set client name](#set-client-name)
    - [Kill client](#kill-client)
    - [Config password](#config-password)
    - [Authenticate password](#authenticate-password)
  - [Geospatial](#geospatial)
    - [Add Geo](#add-geo)
    - [Generate the hash value based on key](#generate-the-hash-value-based-on-key)
    - [List the long and lat based on key](#list-the-long-and-lat-based-on-key)
    - [Get the distance between two location (keys)](#get-the-distance-between-two-location-keys)
    - [Get the radius based on long and lat](#get-the-radius-based-on-long-and-lat)
    - [Get radius by member](#get-radius-by-member)
  - [Benchmark](#benchmark)
- [Contact](#contact)
- [Acknowledgments](#acknowledgments)

## What is Redis?

* Redis stands for **remote dictionary server**
* It is an **in-memory** database, that the data stored on computer's memory
* Often used as **Cache** to improve the application performance
* Used as a NoSQL database
* Also, Redis is a fully-fledged **primary database**
  * It can store and persist multiple data formats for complex applications

## Benefits of a Multi-Model DB (Redis)

* Run and maintain just 1 DB
* Simpler as no need to go through multiple data services -> dealing with microservices
  * No need to go through a lot of setup for multiple data services as all these data services need to be deployed and maintained
* Reduced Latency (Faster)
  * It just go to a single data endpoint and eliminate several internal network hubs. So it can make the application more faster. If there are more number of services that talks to each other, the the latency will be more higher which will cause the applications slower
* Can store different type of data / multiple types of databases in one
* No separate **Cache** needed, as it will act as a cache
* Less complex, as no need to implement a caching layer
* Faster tests
  * Schemaless because it does not need time to initialize the database and build the schema


## How does Redis works support multiple data formats?

* It has the **Redis Core** which is a **key value** store that already supports multiple data types
* You can extend the **Redis Core** with **Redis Modules** for different data types


## Data Persistance & Durability with Redis

### How to keep the data safely persisted?
1. Snapshotting (RDB) -> **.rdb**
    * Produces single-file point-in-time snapshots of your dataset
    * Configure based on time or number of writes/requests passed
    * Snapshots of the data will be stored on a disk
      * To recover the data (Backup & disaster recovery)
      * it will miss the last minute data as snapshot store the data based on 5m - 1h depending on the time

2. Append Only File (AOF) -> **.aof**
    * Logs every write operation continuously in the disk
    * When restarting Redis, it will re-play the AOF to rebuild the state
      * More durable, slower than snapshot

Best: Use both persistence options
* Snapshotting (RDB) - Regular snapshots for DB backups
* Append Only File (AOF) - Persisting all operations one after the other


## How to scale a Redis DB?

* Let's said one of the Redis instance run **out of memory** or **bottleneck**
  * Clustering
    * Having a Primary or Master for reading and writing
    * Setup multiple replicas for reading the data
    * Benefits
      * Handle more requests
      * High availability - if master or primary fails, one of the replicas can take over and the Redis DB still able to work without any issues
    * Drawbacks
      * The more replicas, the more memory space because replicas hold complete copies of Primary Instance's data
      * Only have 1 node (server)
      * If server fails, then the whole Redis DB is gone
  * Sharding (Best method to scale, just that need to manage it)
    * Divide Datasets into smaller shards where each shard is responsible (read/write) for its own subset of data
    * Each shard only needs less memory
    * You can re-shard it into smaller chunks and create more shards if having more data
    * Benefits
      * Multiple Nodes (Server) for handing different shards
        * 1 Node handling 1 Shard
      * Multiple Replicas
      * Sharded
      * Good performance
      * High availability


## Commands Reference

### Start the Redis server

```sh
sudo service redis-server start
```

### Connect to Redis

```sh
redis-cli 
127.0.0.1:6379> ping
PONG
```

### Strings

#### Create a new variable

```sh
set key value
```

#### Create multiple key-value pair variables

```sh
mset key value [key value ...] ~ mset key value lang eng tech programming
```

#### Create a variable that will be expired in how many seconds

```sh
setex key seconds value ~ setex name 10 sheldon
```

#### Create a variable if the variable is not exists

```sh
setnx key value
```

#### Get a variable

```sh
get key
```

#### Get multiple key-value pair variables

```sh
mget key [key ...] ~ mget lang tech
```

#### Get the first num characters

```sh
getrange key int_start int_end ~ getrange email 0 5
```

#### Get length of string

```sh
strlen key
```

#### increment by 1 - incr will always increase by 1

```sh
incr key
```

#### increment by number

```sh
incrby key increment_value
```

#### decrement by 1 - decr will always decrease by 1

```sh
decr key
```

#### decrement by number

```sh
decrby key decrement_value
```

#### increment float

```sh
incrbyfloat key increment_float_value
```

#### Delete the variable in total seconds

```sh
expire key seconds ~ expire email 10
```

#### Check the variable left how many seconds to be deleted

```sh
ttl key
```

### List all the variables that had set

```sh
keys *
```

### Delete all variables that had set

```sh
flushall
```

### Lists

#### Left Push element to lists (Sounds like Stack Push)

```sh
lpush key element [element ...] ~ lpush country USA Singapore Malaysia
```

#### Right Push element to lists (Sounds like Queue Push)

```sh
rpush key element [element ...] ~ rpush country India Poland
```

#### Get the list of data based on range

```sh
lrange key start stop ~ lrange country 0 -1 (0 until -1 is to get all the data)
```

#### Get the length of the lists

```sh
llen key
```

#### Left Pop element (Pop the first element)

```sh
lpop key
```

#### Right Pop element (Pop the last element)

```sh
rpop key
```

#### Change the value of Lists index element

```sh
lset key index value ~ lset country 0 Poland
```

#### Insert the value before/after the element

```sh
linsert key before/after pivot value ~ linsert country before Poland China
Note: Pivot = value exists lists
```

#### Get the value using index

```sh
lindex key index
```

#### Push to the lists if the lists exists

```sh
lpushx key element [element ...]
rpushx key element [element ...]
```

#### Sort the data

```sh
sort key [pattern] ~ sort country alpha / sort country desc alpha
```

#### remove 1 element in the lists if the key exists, else, will be terminated after the timeout

```sh
blpop key timeout
```

### Sets

#### Add to sets

```sh
sadd key element [element...]
```

#### List all data in sets

```sh
smembers key
```

#### Get the length of the sets

```sh
scard key
```

#### Search data exists in sets

```sh
sismember key value ~ return 1 if exists else 0
```

#### Get the differences between multiple sets

```sh
sdiff key [key ...]
```

#### Store the differences between multiple sets into new sets

```sh
sdiffstore destination key [key ...] ~ sdiffstore new_set technology frontend
```

#### Get the intersection element between sets

```sh
sinter key [keys...]
```

#### Store the intersections between multiple sets into new sets

```sh
sinterstore destination key [key ...] ~ sinterstore new_set technology frontend
```

#### Get the union element between sets

```sh
sunion key [keys...]
```

#### Store the unions between multiple sets into new sets

```sh
sunionstore destination key [key ...] ~ sunionstore new_set technology frontend
```

### Sorted Sets

#### Add to sorted sets

```sh
zadd key score member [score member ...] ~ zadd users 1 karchun
```

#### List all data in sorted sets

```sh
zrange key start end ~ zrange users 0 1
```

#### Get the length of sorted sets

```sh
zcard key
```

#### Get the length of sorted sets based on min and max

```sh
zcount key min max
```

#### Remove element from sorted sets

```sh
zrem key member [member ...]
```

#### Reverse the sorted sets

```sh
zrevrange key start stop ~ zrevrange users 0 -1
```

#### Get the score of the member

```sh
zscore key member
```

#### Reverse the sorted sets based on score

```sh
zrevrangebyscore key max min
```

#### Increase the score value by member

```sh
zincrby key increment_value member
```

#### Remove the data by range of score

```sh
zremrangebyscore key min_score max_score
```

#### Remove the data by rank

```sh
zremrangebyrank key min max
```

### HyperLogLog

probabilistic data structured used to count unique values ~ suitable for sets

#### Add data to hyperloglog

```sh
pfadd key element [element ...]
```

#### Get the length of hyperloglog

```sh
pfcount key [key ...]
```

#### Merge multiple hyperloglog to new hyperloglog

```sh
pfmerge destkey sourcekey [sourcekey ...]
```

### Hashes

#### Add new hastset key-value pair

```sh
hset key hash_key hash_value [hash_key hash_value]
```

#### Get all the hash keys from key

```sh
hkeys key
```

#### Get all the hash values from key

```sh
hvals key
```

#### Get all hash keys and values from key

```sh
hgetall key
```

#### Check hash keys exists

```sh
hexists key hash_key
```

#### Get length of hash

```sh
hlen key
```

#### Add multiple hashset key-value pairs

```sh
hmset key hash_key hash_value [hash_key hash_value...]
```

#### Get multiple hashset key-value pairs

```sh
hmget key hash_key [hash_key ...]
```

#### Increment the hash_value by number

```sh
hincrby key hash_key increment_value
```

#### Delete hash_key

```sh
hdel key hash_key
```

### Transactions

- helpful to execute multiple commands
```sh
multi
list_of_commands Examples:
- set name hello
- get name
- set a 1
- set b 2

optional: watch key [key ...]
optional: discard ~ discard the transactions

exec ~ execute the whole list of commands
```

### PubSub

- Published and subscriber 

1. First setup the subscriber first then only publisher
Subscriber
```sh
subscribe channel [channel ...]
```

2. Publish the message
Published
```sh
publish channel message
```

#### Setup subscriber with pattern

```sh
psubscribe pattern ~ psubscribe news* h?llo b[ai]ll --- new1 or anything can work
-> * means all
-> ? means can be replaced by any char
-> [ai] means particular characters will be matched
```

#### Display all channels without pattern subscribers

```sh
pubsub channels
```

#### Get the total of subscribers from that channels

```sh
pubsub numsub channel_name [channel_name]
```

#### Get the total of pattern channels 

```sh
pubsub numpat
```

### Connection & Security

#### Switch to different database connection

```sh
redis-cli
ping
select 0...999  ~ 0 is the first database (default), 1 is the first one
```

#### List all the client

```sh
client list
```

#### Set client name

```sh
client setname client_name
```

#### Kill client

```sh
client kill id id_number
```

#### Config password

```sh
config set requirepass "password"
```

#### Authenticate password

```sh
auth "password"
```

### Geospatial

- Store geography details as sorted sets
- So you can use the commands of sorted sets to perform the tasks

#### Add Geo

```sh
geoadd key long lat "member" [long lat member ...]
```

#### Generate the hash value based on key

```sh
geohash key member [member ...]
```

#### List the long and lat based on key

```sh
geopos key member [member ...]
```

#### Get the distance between two location (keys)

```sh
geodist key "member1" "member2" [M|KM|FT|MI]
```

#### Get the radius based on long and lat

```sh
georadius key long lat radius M|KM|FT|MI ~ georadius maps 72.. 75.. 500 KM
```

#### Get radius by member

```sh
georadiusbymember key member radius M|KM|FT|MI
```

### Benchmark

- simulates running commands done by N clients at the same time sending M total queries

```sh
redis-benchmark -n 1000 ~ send 1000 commands
redis-benchmark -n 1000 -d 100000 ~ send 1000 commands with 100kb size
redis-benchmark -n 1000 -d 100000 -c 100 ~ send 1000 commands with 100kb size, and with 100 clients
```

## Contact

Tan, Kar Chun - [LinkedIn](https://www.linkedin.com/in/karchuntan/) - karchuntan.1999@gmail.com


## Acknowledgments

* [Redis](https://redis.io/)
