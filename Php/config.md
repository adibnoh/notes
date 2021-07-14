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

## Set Rlimit

```conf

; equal to soft limit files
rlimit_files = 1024

```

### Calculate Process

#### Estimate Max Server / Max Children

Assume Php server has capacity of 4gb Ram, and each of Php process take up 30mb

formula: `(1024*<total_gigabyte_allocated>)/30 = <nearest_estimated_max_server_count>`

`(1024*4) / 30 = 136.53`, we can round it up to 130 max server

#### Estimate start_servers

For pm.start_servers, I multiply the number of cores that I have by 4.

4 x 4 = 16

So I set pm.start_servers to 16.

If you have 8 cores, then it will be: 4 x 8 = 32.

#### Estimate min_spare_servers

For pm.min_spare_servers, multiply the number of cores that you have by 2.

In my case, that is 2 x 4 = 8.

So I set pm.min_spare_servers to 8.

#### Estimate max_spare_servers

For pm.max_spare_servers, multiply the number of cores on your server by 4.

On my machine, that is 4 x 4 = 16.

So I set pm.max_spare_servers to 16, the same value that I used for pm.start_servers.

#### Estimate max request

* [ ] TODO

##### Config with description

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

## Error Log

default path is (if using nginx):

`/var/log/nginx/graduan.com-error.log`

## Reference

* [PHP-FPM: Process Management](https://serversforhackers.com/c/php-fpm-process-management)
* [PHP-FPM settings tutorial. max_servers, min_servers, etc.](https://thisinterestsme.com/php-fpm-settings/)