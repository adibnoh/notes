# Init

## Installation

### Vagrant

[https://atlas.hashicorp.com/centos/boxes/7](https://atlas.hashicorp.com/centos/boxes/7)

```txt

-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory

```

`yum reinstall glibc-common`

## Fetch all available package

`yum -y update`

## Nginx

[https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7)

Add CentOS 7 EPEL repository

`sudo yum install epel-release`

Install nginx

`sudo yum install nginx`

Start Nginx

`sudo systemctl start nginx`

Run nginx when server start

`sudo systemctl enable nginx`

## Maria DB

Install Maria DB

`sudo yum install mariadb-server mariadb`

Start Maria DB

`sudo systemctl start mariadb`

Change root password

`sudo mysql_secure_installation`

Run mariadb when server start

`sudo systemctl enable mariadb`

## Nano

Install nano

`sudo yum install nano`

## Php

Install PHP

Subscribing to the IUS Community Project Repository

`cd ~`

`curl 'https://setup.ius.io/' -o setup-ius.sh`

`sudo bash setup-ius.sh`

Install PHP

`sudo yum install php70u-fpm-nginx php70u-cli php70u-mysqlnd`

Configure PHP

`sudo nano /etc/php-fpm.d/www.conf`

Look for the block containing listen = 127.0.0.1:9000, which tells PHP-FPM to listen on the loopback address at port 9000. Comment this line with a semicolon, and uncomment 

`listen = /run/php-fpm/www.sock a few lines below`

Next, look for the block containing listen.acl_users values, and uncomment listen.acl_users = nginx:

Next, make sure that Nginx is using the correct socket path to handle PHP files. Start by opening /etc/nginx/conf.d/default.conf

`sudo nano /etc/nginx/conf.d/php-fpm.conf`

php-fpm.conf defines an upstream, which can be referenced by other Nginx configuration directives. Inside of the upstream block, use a # to comment out server 127.0.0.1:9000;, and uncomment server unix:/run/php-fpm/www.sock;

Restart php and nginx

`sudo systemctl restart php-fpm`

`sudo systemctl restart nginx`

Failed to mount folders in Linux guest. This is usually because the "vboxsf" file system is not available
[https://github.com/dotless-de/vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest)

## Reference

* [https://www.digitalocean.com/community/tutorials/how-to-configure-logging-and-log-rotation-in-nginx-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-configure-logging-and-log-rotation-in-nginx-on-an-ubuntu-vps)
* [https://www.linode.com/docs/websites/nginx/how-to-configure-nginx](https://www.linode.com/docs/websites/nginx/how-to-configure-nginx)
* [https://www.godaddy.com/garage/tech/config/how-to-install-and-configure-nginx-on-centos-6/](https://www.godaddy.com/garage/tech/config/how-to-install-and-configure-nginx-on-centos-6/)
* [https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7)