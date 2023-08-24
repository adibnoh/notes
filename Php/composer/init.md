# Init

## Downgrade to specific version

`composer self-update <your_desired_version>`

`composer self-update 1.10.13`

## Check Global Composer version

`composer -V`

## Upgrade Global Composer to latest version

`composer self-update`

## Reinstall package

`rm -rf vendor && composer install`

## Issue

### Run out of memory

`php -d memory_limit=-1 '<composer_path>' <composer_command>`

eg:

`php -d memory_limit=-1 'which composer' update`