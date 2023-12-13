# Init

### Show All Process

`SHOW FULL PROCESSLIST;`

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

[How do I enable the MySQL slow query log? [duplicate]](https://stackoverflow.com/questions/22609257/how-do-i-enable-the-mysql-slow-query-log)

## Disable SQL Mode

Only run this features in Sequel Pro

`SET SQL_MODE = '';` - disable sql mode in current connection, when disconnect and reconnect to previous connection all sql mode will return to normal

`SHOW VARIABLES LIKE 'sql_mode'` - check default sql mode

## Show max allowed packet

`SHOW VARIABLES LIKE 'max_allowed_packet';`

## Issues

Mysql usage more than 100%

[MySQL process goes over 100% of CPU usage](https://serverfault.com/questions/220188/mysql-process-goes-over-100-of-cpu-usage)

## Reference

* [How To Set Up a Remote Database to Optimize Site Performance with MySQL](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-database-to-optimize-site-performance-with-mysql)
* [How To Create a New User and Grant Permissions in MySQL](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)
* [MySQLTuner-perl](https://github.com/major/MySQLTuner-perl)