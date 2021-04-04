# Opcache

Edit opcache config in php fpm config file

```ini

opcache.enable=1

opcache.revalidate_freq=0
opcache.validate_timestamps=0

; Depend on number of php files existed in your project
; find <path_to_project_folder> -type f -iname *.php | wc -l
; if number of files is 11367, round it to largest, so 12000
opcache.max_accelerated_files=12000

opcache.memory_consumption=512
opcache.interned_strings_buffer=64
opcache.fast_shutdown=1

opcache.save_comments=1
opcache.dups_fix=1

```

## Laravel

Install package - `composer require appstract/laravel-opcache`

when new code is deployed run:

```bash
php artisan opcache:clear && 
php artisan route:cache && 
php artisan config:cache && 
php artisan view:cache && 
php artisan opcache:compile --force
```

Ensure the application is not in maintenance mode when compiling Opcache.

## Reference

* [Best Zend OpCache Settings/Tuning/Config](https://www.scalingphpbook.com/blog/2014/02/14/best-zend-opcache-settings.html)
* [Zend OPcache - Configuration Directives]s(http://files.zend.com/help/Zend-Server/content/zendserverapi/zend_opcache-configuration_directives.htm)
* [Fine-Tune Your Opcache Configuration to Avoid Caching Suprises](https://tideways.com/profiler/blog/fine-tune-your-opcache-configuration-to-avoid-caching-suprises)
* [Make your Laravel App Fly with PHP OPcache](https://medium.com/appstract/make-your-laravel-app-fly-with-php-opcache-9948db2a5f93#.bjrpj4h1c)