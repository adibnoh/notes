# Php

## php

`brew install php`

## php 7.2

`brew install php@7.2`

## Switch version

`brew unlink php`

`brew services stop php`

`brew services start php@7.2`

`brew link php@7.2`

and vice versa

and ensure php actually stop running, run `brew services list`. If your php is run by root, you might need to sudo to turn it off.

might need to restart valet after php version is changed 

## Install Extension

Brew no longer support install with option

### PhpRedis

Need to use pecl to install PhpRedis

`pecl install redis`

edit `php.ini`

```

extension=<path_to_redis.so>/redis.so

```

restart php

### Imagick

Install Imagick via Brew

`brew install pkg-config imagemagick`

Compile Imagick PHP extension with pecl

`pecl install imagick`

edit `php.ini`

```

extension=<path_to_redis.so>/imagick.so

```

restart php

### Install IMAP Extension

`brew tap kabel/php-ext`

`brew install php@7.2-imap` - for php version 7.2

`brew install php-imap` - for current php version

## Restart Php

`brew services restart php`

Change php version accordingly

## Upgrade Php

`brew upgrade php`

After each upgrade, need to reinstall all Php extension manually and update their path in `php.ini` .

## References

* [Php Redis](https://github.com/phpredis/phpredis)
* [PHP 7.2 extensions](https://github.com/kabel/homebrew-php-ext/issues/1)
* [Install PHP’s imagick extension on Mac with Brew](https://ma.ttias.be/install-phps-imagick-extension-on-mac-with-brew/)