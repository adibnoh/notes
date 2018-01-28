# Mysql 5.7

## Install Mysql

`sudo apt-get install mysql-server`

## Run secure setup

`sudo mysql_secure_installation`

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

Reference:

https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-database-to-optimize-site-performance-with-mysql

https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql
