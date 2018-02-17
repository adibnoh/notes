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

## Reference

* [https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04)