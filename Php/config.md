# Config

## CLI

## FPM

File location

`/etc/php/7.2/fpm/pool.d/www.conf` - vary according to your Php version

```conf


pm.max_children = 5
pm.start_servers = 2
pm.min_spare_servers = 1
pm.max_spare_servers = 3
pm.max_requests = 500

slowlog = /var/log/php7.2.log.slow
request_slowlog_timeout = 10s


```

Restart Php after config file has been updated

`service php7.2-fpm restart`

### Calculate Process

Assume Php server has capacity of 4gb Ram, and each of Php process take up 30mb

`(1024*4) / 30 = 136.53`, we can round it up to 130 max server

```conf

pm.max_children = 130 # The hard-limit total number of processes allowed
pm.start_servers = 20 # When php-fpm starts, have this many processes waiting for requests
pm.min_spare_servers = 10 # Number spare processes php-fpm will create
pm.max_spare_servers = 20 # Max number of spare (waiting for connections) processes allowed to be created
pm.process_idle_timeout = 10s;

```

## INI

Locate php ini location

`php -i | grep php.ini`

```conf

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

; Must be greater than or equal to upload_max_filesize
post_max_size = 8M


;opcache.enable=1
;opcache.memory_consumption=128
;opcache.interned_strings_buffer=8
;opcache.max_accelerated_files=10000
;opcache.validate_timestamps=1
;opcache.save_comments=1


```

Restart Php after config file has been updated

`service php7.2-fpm restart`