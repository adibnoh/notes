# Init

## Installation

Create and enter Project Directory

`mkdir <project_directory>`

`cd /<project_directory>`

Install Laravel Installer Globally via Composer

`composer global require "laravel/installer"`

`laravel new`

Create environment file

`cp .env.example .env`

Regenerate Application Key

`php artisan key:generate`

Set user group to www-data

`sudo chgrp -R www-data <project_directory>`

## Common Issue

### Allow Web Server to write at Storage and Bootstrap directory

add owner of current project folder to www-data group

`sudo usermod -a -G <group> <username>`

Give the webserver the rights to read and write to storage and cache

`sudo chmod -R ug+rwx storage bootstrap/cache`

### Cannot run Global Laravel Ins`taller

`composer global require "laravel/installer"`

```txt
laravel/installer v1.5.0 requires ext-zip * -> the requested PHP extension zip is missing from your system.
```

Solution

`sudo apt-get install php-zip`

### Cannot Install Laravel via Laravel Installer

`laravel new`

```txt
laravel: command not found
```

Solution

`nano ~/.bash_profile`

paste

`export PATH=~/.composer/vendor/bin:$PATH`

## Reference