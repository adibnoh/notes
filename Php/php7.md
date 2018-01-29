## Init

This command will install default php version - right now php 7.0

`sudo apt-get install php`

This additional php extension below is for Laravel dependencies

`sudo apt-get install php-zip`
`sudo apt-get install php-mbstring`
`sudo apt-get install php-xml`

## Install Composer

`apt-get install composer`

## Show php info

`php -i | grep "Loaded Configuration File”`

## Config File 

`sudo nano /etc/php/7.0/cli/php.ini`

## Common Issues

### Cannot run Global Laravel Installer

`composer global require "laravel/installer"`

```
laravel/installer v1.5.0 requires ext-zip * -> the requested PHP extension zip is missing from your system.
```

Solution

`sudo apt-get install php-zip`

### Cannot Install Laravel via Laravel Installer

`laravel new`

```
laravel: command not found
```

Solution

`echo 'export PATH="$PATH:$HOME/.config/composer/vendor/bin"' >> ~/.bashrc`

`source ~/.bashrc`



