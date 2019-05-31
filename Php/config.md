# Config

## FPM Config

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

## Php Ini

File location

`/etc/php/7.2/cli/php.ini`

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