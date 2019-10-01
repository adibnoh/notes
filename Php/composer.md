# Composer

## Reinstall package

`rm -rf vendor && composer install`

## Issue

### Run out of memory

`php -d memory_limit=-1 '<composer_path>' <composer_command>`

eg:

`php -d memory_limit=-1 'which composer' update`