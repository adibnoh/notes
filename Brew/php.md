# Php

## Install

### php

`brew install php`

### php 7.2

`brew install php@7.2`

## Switch version

`brew unlink php`

`brew services stop php`

`brew services start php@7.2`

`brew link php@7.2`

and vice versa

and ensure php actually stop running, run `brew services list`. If your php is run by root, you might need to sudo to turn it off.

might need to restart valet after php version is changed 

`brew install php@7.4`

## Imagick

* brew install imagemagick
* pecl install imagick

restart valet

### PhpRedis

Need to use pecl to install PhpRedis

`pecl install redis`

edit `php.ini`

```

extension=<path_to_redis.so>/redis.so

```

restart php

## Pecl Installation Directory

`pecl config-get ext_dir`

## Restart Php

`brew services restart php`

## Upgrade Php

`brew upgrade php`

After each upgrade, need to reinstall all Php extension manually and update their path in `php.ini`.

### Imap

https://stackoverflow.com/a/51584213

## References

* [Php Redis](https://github.com/phpredis/phpredis)
* [Configuring error on masOS Mojave](https://github.com/Imagick/imagick/issues/289#issuecomment-500951481)
* [Installing Homebrew PHP extensions with PECL](https://grrr.tech/posts/installing-homebrew-php-extensions-with-pecl/)