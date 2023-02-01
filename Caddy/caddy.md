# Caddy

## Cloudflare

Ensure SSL/TLS encryption is set to full mode

## Install

https://caddyserver.com/docs/install#debian-ubuntu-raspbian

After installation, run `caddy stop`. This is to ensure there is no port is in use.

## Caddyfile

Most of my project is Laravel and it is much easier to use Caddyfile to store all neccessary configuration.

```Caddyfile

my-website.com {
    # Resolve the root directory for the app
    root * /var/www/my-website/public

    # Provide Zstd and Gzip compression
    encode zstd gzip

    # Allow caddy to serve static files
    file_server

    # Enable PHP-FPM
    php_fastcgi unix//run/php/php7.4-fpm.sock
}

```

## References

https://ohdear.app/news-and-updates/how-we-used-caddy-and-laravels-subdomain-routing-to-serve-our-status-pages

https://laravel-news.com/unlimited-custom-domains-vapor

https://caddyserver.com/docs/caddyfile-tutorial

https://jorgeglz.io/blog/setting-up-laravel-applications-with-caddy-2/

https://caddy.community/t/serving-tens-of-thousands-of-domains-over-https-with-caddy/11179
