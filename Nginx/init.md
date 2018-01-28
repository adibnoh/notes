## Install Nginx

`sudo apt-get install nginx`

## Firewall Settings

### Allow HTTP and OpenSSH

`sudo ufw allow 'Nginx HTTP'`

`sudo ufw allow 'OpenSSH'`

If encounterred error

```
ERROR: Could not find a profile matching 'OpenSSH'
```

`sudo apt-get install ssh`

## Enable Firewall

`sudo ufw enable`

### Verify Firewall Status

`sudo ufw status`

## Verify Nginx Status

`service nginx status`

## Setup Server Block

### Edit default block

`sudo nano /etc/nginx/sites-available/default`

```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /home/<username>/default;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }
}
```

Create test file in default folder - assume we login in as user at their root folder

`mkdir default`

`cd default`

`nano index.php`

```php
<?php

phpinfo();

```

Duplicate default block and create new block
Replace example.com with your domain name

`sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/example.com`

`sudo nano /etc/nginx/sites-available/example.com`

Remove default_server

```
server {
        listen 80;
        listen [::]:80;

        root /home/<username>/example.com;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name example.com www.example.com;

        location / {
                try_files $uri $uri/ =404;
        }
}
```

Setting for Laravel

```
server {
        listen 80;
        listen [::]:80;

        root /home/<username>/example.com;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name example.com www.example.com;

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        }

        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }
}
```

### Enable server block

`sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/`

### Avoid a possible hash bucket memory problem

`sudo nano /etc/nginx/nginx.conf`

edit this line

`server_names_hash_bucket_size 64;`

### Check Nginx Configuration

`sudo nginx -t`

## Restart Nginx

`sudo service nginx restart`

## Modify Your Local Hosts File for Testing

In your local mac

`sudo nano /etc/hosts`

Append this line

```
<server_ip_address> example.com www.example.com
```

## Reference:

https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04

https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-in-ubuntu-16-04

https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-server-blocks-virtual-hosts-on-ubuntu-16-04

https://askubuntu.com/questions/823703/openvpn-setting-up-own-server-2-errors


