## Installation

Create and enter Project Directory, then install Laravel

`mkdir <project_directory>`

`cd /<project_directory>`

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