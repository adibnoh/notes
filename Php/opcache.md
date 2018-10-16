# Opcache

```conf

opcache.revalidate_freq=0
opcache.validate_timestamps=0 (comment this out in your dev environment)

; Depend on number of php files existed in your project
; find <path_to_project_folder> -type f -iname *.php | wc -l
opcache.max_accelerated_files=7963

opcache.memory_consumption=192
opcache.interned_strings_buffer=16
opcache.fast_shutdown=1

```

## Reference

* [Best Zend OpCache Settings/Tuning/Config](https://www.scalingphpbook.com/blog/2014/02/14/best-zend-opcache-settings.html)
* [Zend OPcache - Configuration Directives]s(http://files.zend.com/help/Zend-Server/content/zendserverapi/zend_opcache-configuration_directives.htm)
* [Fine-Tune Your Opcache Configuration to Avoid Caching Suprises](https://tideways.com/profiler/blog/fine-tune-your-opcache-configuration-to-avoid-caching-suprises)