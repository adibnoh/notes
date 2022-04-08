# Cheat Sheet

Grap value form Php info from command line

`php -r 'phpinfo();' | grep 'memory_limit'`

List all extension

`php -m`

## Parse Boolean

```php

$bool = filter_var($value, FILTER_VALIDATE_BOOLEAN);

```

## How can I put strings in an array, split by new line?

```php

$string = "My text1
My text2
My text3";

$array = preg_split("/\r\n|\n|\r/", $string);

```

[https://stackoverflow.com/a/11165332](https://stackoverflow.com/a/11165332)

## Reference

* [Parsing a string into a boolean value in PHP](https://stackoverflow.com/questions/4775294/parsing-a-string-into-a-boolean-value-in-php)