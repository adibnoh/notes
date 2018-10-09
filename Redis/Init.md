# Init

## Restart/Stop/Start Server

`/etc/init.d/redis-server restart`

`/etc/init.d/redis-server stop`

`/etc/init.d/redis-server start`

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

## Reference

* [Redis configuration for production](https://scaleyourcode.com/blog/article/15)