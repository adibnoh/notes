# Config

## Global config file

`/etc/mysql/my.cnf`

## Specific user config file

`~/.my.cnf`

## Config file content

Lets say your database server is 1G Ram

```conf

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#

[mysqld]

key-buffer-size                = 1.5G # 25% from allocated RAM
max-connections                = 1500 # refer https://www.mysqlcalculator.com/

table-open-cache = 4000 # should be higher than opened_tables value -> check value by running `SHOW GLOBAL STATUS LIKE 'Opened_tables';'`

# LOGGING #
log-error                      = /var/lib/mysql/mysql-error.log
slow-query-log                 = 1
slow-query-log-file            = /var/lib/mysql/mysql-slow.log
long-query-time                = 10
log-queries-not-using-indexes  = off

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

```

Restart mysql after config file is updated

`/etc/init.d/mysql restart`