# Init

## Install Nginx

`sudo apt-get install nginx`

## Firewall Settings

### Allow HTTP and OpenSSH

`sudo ufw allow 'Nginx HTTP'`

`sudo ufw allow 'OpenSSH'`

If encountered error

```log
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

```conf
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

```conf
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

```conf
server {
        listen 80;
        listen [::]:80;

        root /home/<username>/example.com/public;
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

```conf
<server_ip_address> example.com www.example.com
```

### Redirect www to non-www

```conf

server {
        
        ...

        if ($host = www.domain.com) {
                return 301 https://domain.com$request_uri; // this redirect to https, if you wish to redirect to non-ssl site, change accordingly
        }

        ...
}

```

or

```

server {
    server_name  www.mydomain.com;
    return       301 https://mydomain.com$request_uri;
}

```

whichever works

### Add user to www-data

List all user in www-data

`grep ^www-data /etc/group`

add user in www-data group

`sudo adduser <user> www-data`


### 

```conf

server {

        location ~* .(jpg|jpeg|png|gif|ico|css|js)$ {
            expires 365d;
        }

        server_tokens off;

        #GZIP
        # Enable gzip compression.
        gzip on;                                                                  
                                                                            
        # Compression level (1-9).                                                 
        # 5 is a perfect compromise between size and CPU usage, offering about     
        # 75% reduction for most ASCII files (almost identical to level 9).        
        gzip_comp_level    5;                                                      
                                                                                
        # Don't compress anything that's already small and unlikely to shrink much 
        # if at all (the default is 20 bytes, which is bad as that usually leads to
        # larger files after gzipping).                                            
        gzip_min_length    256;                                                    
                                                                                
        # Compress data even for clients that are connecting to us via proxies,    
        # identified by the "Via" header (required for CloudFront).                
        gzip_proxied       any;     

         # Tell proxies to cache both the gzipped and regular version of a resource
        # whenever the client's Accept-Encoding capabilities header varies;
        # Avoids the issue where a non-gzip capable client (which is extremely rare
        # today) would display gibberish if their proxy gave them the gzipped version.
        gzip_vary          on;

        # Compress all output labeled with one of the following MIME-types.
        gzip_types
        application/atom+xml
        application/javascript
        application/json
        application/ld+json
        application/manifest+json
        application/rss+xml
        application/vnd.geo+json
        application/vnd.ms-fontobject
        application/x-font-ttf
        application/x-web-app-manifest+json
        application/xhtml+xml
        application/xml        
        font/opentype
        image/bmp
        image/svg+xml
        image/x-icon
        text/cache-manifest
        text/css
        text/plain
        text/vcard
        text/vnd.rim.location.xloc
        text/vtt
        text/x-component
        text/x-cross-domain-policy;
        # text/html is always compressed by gzip module                                       

}

```

## Reference

* [How To Install Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04)
* [How To Install Linux, Nginx, MySQL, PHP (LEMP stack) in Ubuntu 16.04](https://www.digitalocean.caom/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-in-ubuntu-16-04)
* [How To Set Up Nginx Server Blocks (Virtual Hosts) on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-server-blocks-virtual-hosts-on-ubuntu-16-04)
* [OpenVPN setting up own server 2 errors](https://askubuntu.com/questions/823703/openvpn-setting-up-own-server-2-errors)
* [NGINX redirect www to non-www](https://www.digitalocean.com/community/questions/nginx-redirect-www-to-non-www-e1f70f55-b31d-4612-bc14-e31c3cfece26)