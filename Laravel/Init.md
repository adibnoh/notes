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

## Common Issue

### Allow Web Server to write at Storage and Bootstrap directory

add owner of current project folder to www-data group

`sudo usermod -a -G <group> <username>`

Give the webserver the rights to read and write to storage and cache

`sudo chgrp -R www-data storage bootstrap/cache`

`sudo chmod -R ug+rwx storage bootstrap/cache`

### Cannot run Global Laravel Installer

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

`echo 'export PATH="$PATH:$HOME/.config/composer/vendor/bin"' >> ~/.bashrc`

`source ~/.bashrc`

## Reference