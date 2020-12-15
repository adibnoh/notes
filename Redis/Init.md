# Init

## Install

Just follow this instruction

[How To Install and Configure Redis on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04)

## Restart/Stop/Start Server

`/etc/init.d/redis-server restart`

`/etc/init.d/redis-server stop`

`/etc/init.d/redis-server start`

## CLI

run `redis-cli` to enter redis command line mode

you may run any redis operation here.

### Check Version

`INFO`

## Config

`nano /etc/redis/redis.conf`

Default Config

[Default Config](http://download.redis.io/redis-stable/redis.conf)

### Persisting to Disk

By default Redis will create snapshot after certain condition meet, we may disable snapshot if we don't care about data loss.

Default config

```conf

save 900 1 # This command means if 15 minutes (900 seconds) go by and at least 1 change was made, create a snapshot.
save 300 10
save 60 10000

```

Disable snapshot

```conf

# save 900 1 # comment out all snapshot
# save 300 10
# save 60 10000

```

* [4.1.1 Persisting to disk with snapshots](https://redislabs.com/ebook/part-2-core-concepts/chapter-4-keeping-data-safe-and-ensuring-performance/4-1-persistence-options/4-1-1-persisting-to-disk-with-snapshots/)
* [Redis Persistence](https://redis.io/topics/persistence)

### Limit Max Memory

`maxmemory 1gb` - 70% from allocated memory

### Max Memory Policy

if we are intent to use redis as cache set to `maxmemory-policy allkeys-lru` - remove less used keys regardless of the  expire set

### Append Only File persistence

Append Only File will save each operation to log file - if we dont care about data persistence, disable this option

`appendonly no`

## Reference

* [Redis configuration for production](https://scaleyourcode.com/blog/article/15)
* [How To Change Redis's Configuration from the Command Line](https://www.digitalocean.com/community/cheatsheets/how-to-change-redis-configuration)