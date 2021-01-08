# Auto Deploy

## Nginx configuration

`nano /etc/nginx/nginx.conf`

```conf

# if you're login to your server using ssh adib@192.111.111.111 then you can set value here user adib;
# this is to avoid file ownership conflict between git and nginx when you pull source code from git.
user <server_username>;

```

restart nginx - `service nginx restart`

## Php configuration

### TODO

* [ ] need to find a way to run php as login user not www-data

## Git Pull

* `cd <project_path>`
* `git pull origin master`
* `composer install --no-dev --no-scripts`