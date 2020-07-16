# Cheat Sheet

Grap value form Php info from command line

`php -r 'phpinfo();' | grep 'memory_limit'`

List all extension

`php -m`

## Parse Boolean

```php

$bool = filter_var($value, FILTER_VALIDATE_BOOLEAN);

```

## Reference

* [Parsing a string into a boolean value in PHP](https://stackoverflow.com/questions/4775294/parsing-a-string-into-a-boolean-value-in-php)