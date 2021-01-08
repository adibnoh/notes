# Install Mysql 8.* on Ubuntu Server 20.04

## Install

`sudo apt install mysql-server`

`sudo mysql_secure_installation`

Ignore `VALIDATE PASSWORD PLUGIN` - if we enabled this option, adding password will be so difficult

## Create new user and allow remote access

### Login to database

`mysql -u root -p`

### Create user

`CREATE USER 'username'@'%' IDENTIFIED BY 'password';`

### Grant Privilege

`GRANT ALL ON *.* TO 'username'@'%';`

### Flush Privileges

`FLUSH PRIVILEGES;`

Done!, try access database remotely using Sequal Pro

![https://i.imgur.com/1gFrdqC.jpg](https://i.imgur.com/1gFrdqC.jpg)

## Issues

### Cannot Access remotely

Maybe Mysql is strictly bind address to localhost, we can disable binding address to localhost

`sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`

comment out

```

# bind-address=127.0.0.1

```

restart mysql

`sudo service mysql restart` or `sudo /etc/init.d/mysql restart`

## References

* [How To Install Linux, Apache, MySQL, PHP (LAMP) stack on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04)
* [How to restart remote MySQL server running on Ubuntu linux?](https://stackoverflow.com/a/30101686)