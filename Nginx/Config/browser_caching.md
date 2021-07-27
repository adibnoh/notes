# Browser Caching

```conf

. . .
# Default server configuration
#

# Expires map
map $sent_http_content_type $expires {
    default                    off;
    text/html                  epoch;
    text/css                   max;
    application/javascript     max;
    ~image/                    max;
    ~font/                     max;
}

server {
    listen 80 default_server;
    listen [::]:80 default_server;

    expires $expires;
. . .

```

https://www.digitalocean.com/community/tutorials/how-to-implement-browser-caching-with-nginx-s-header-module-on-ubuntu-20-04

## Alternative

```conf

server {

    location ~* .(jpg|jpeg|png|gif|ico|css|js)$ {
        expires 365d;
    }

}

```