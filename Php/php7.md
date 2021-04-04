# Php 7

## Init

This command will install default php version - right now php 7.0

`sudo apt-get install php`

This additional php extension below is for Laravel dependencies

`sudo apt-get install php-zip`

`sudo apt-get install php-mbstring`

`sudo apt-get install php-xml`

## Install Composer

`apt-get install composer`

## Show php info

`php -i | grep "Loaded Configuration File”`

## Config File

`sudo nano /etc/php/7.0/cli/php.ini`

`/etc/php/7.1/fpm/pool.d/www.conf`

## Restart Php

`service php7.1-fpm restart`

## Upgrade

### Install Php7.2

`sudo add-apt-repository ppa:ondrej/php`

if encountered this error

```txt
UnicodeDecodeError: 'ascii' codec can't decode byte 0x* in position *: ordinal not in range(128)
```

run this command

`sudo apt-get install -y language-pack-en-base`
`sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php`

then

`sudo apt-get update`

`sudo apt-get install php7.2`

`sudo apt-get install php7.2-mysql`

`sudo apt-get install php7.2-fpm`

`sudo apt-get install php7.2-mysql`

`sudo apt-get install php7.2-imagick`

## Logs

Trace slow php script

* [Debugging PHP Scripts Using slow_log and more](https://easyengine.io/tutorials/php/fpm-slow-log/)
* [PHP-FPM: Process Management](https://serversforhackers.com/c/php-fpm-process-management)

Logs location

`/var/log/php7.1-fpm.log`

`/var/log/php7.1.log.slow` - custom

## Php config

edit php.ini

```conf

...

; Maximum allowed size for uploaded files.
upload_max_filesize = 40M

; Must be greater than or equal to upload_max_filesize
post_max_size = 40M

...

```

## Issues

### child  exited with code 0 after  seconds from start

if encounter this error message just ignore them

### References

* [How to Read the PHP Slow Request Log](https://serverpilot.io/community/articles/how-to-read-the-php-slow-request-log.html)
* [Wordpress 502 & 504 Errors NGINX & PHP-FPM](https://www.digitalocean.com/community/questions/wordpress-502-504-errors-nginx-php-fpm)
* [Adjusting child processes for PHP-FPM (Nginx)](https://myshell.co.uk/blog/2012/07/adjusting-child-processes-for-php-fpm-nginx/)

## References

* [How To Upgrade to PHP 7 on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04)
* [Determining the correct number of child processes for PHP-FPM on NGinx](https://www.kinamo.be/en/support/faq/determining-the-correct-number-of-child-processes-for-php-fpm-on-nginx)
* [PHP-FPM: Process Management](https://serversforhackers.com/c/php-fpm-process-management)