# Init

Mysql 5.7

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

## Logs

### Enable slow query log

Version 5.1.6 and above:

Enter the MySQL shell and run the following command:

`set global slow_query_log = 'ON';`

Set the path to the slow query log:

`set global slow_query_log_file ='/var/log/mysql/slow-query.log';`

Set the amount of time a query needs to run before being logged:

`set global long_query_time = '20';` (default is 10 seconds)

Confirm the changes are active by entering the MySQL shell and running the following command:

`show variables like '%slow%';`

![https://stackoverflow.com/questions/22609257/how-do-i-enable-the-mysql-slow-query-log](https://stackoverflow.com/questions/22609257/how-do-i-enable-the-mysql-slow-query-log)

## Disable SQL Mode

Only run this features in Sequal Pro

`SET SQL_MODE = '';` - disable sql mode in current connection, when disconnect and reconnect to previous connection all sql mode will return to normal

`SHOW VARIABLES LIKE 'sql_mode'` - check default sql mode

## Issues

Mysql usage more than 100%

[https://serverfault.com/questions/220188/mysql-process-goes-over-100-of-cpu-usage](https://serverfault.com/questions/220188/mysql-process-goes-over-100-of-cpu-usage)

## Reference

* [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-database-to-optimize-site-performance-with-mysql](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-database-to-optimize-site-performance-with-mysql)
* [https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)