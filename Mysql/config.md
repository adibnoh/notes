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

# SAFETY #
max-allowed-packet             = 16M
max-connect-errors             = 100
skip-name-resolve
sql-mode                       = ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION

# CACHES AND LIMITS #
key-buffer-size                = 16M
tmp-table-size                 = 16M
max-heap-table-size            = 16M
query-cache-type               = 0
query-cache-size               = 16M
max-connections                = 151
thread-stack                   = 196608
thread-cache-size              = 8
open-files-limit               = 5000
table-definition-cache         = 1400
table-open-cache               = 2000

# INNODB #
innodb-flush-method            = 0
innodb-log-files-in-group      = 2
innodb-log-file-size           = 50M
innodb-flush-log-at-trx-commit = 1
innodb-file-per-table          = 1
innodb-buffer-pool-size        = 128M
innodb-log-buffer-size         = 16M

innodb-io-capacity = 200
innodb-io-capacity-max = 2000
innodb-read-io-threads = 4
innodb-thread-concurrency = 4
innodb-write-io-threads = 4

# LOGGING #
log-error                      = /var/lib/mysql/mysql-error.log
log-queries-not-using-indexes  = 1
slow-query-log                 = 1
slow-query-log-file            = /var/lib/mysql/mysql-slow.log
long-query-time                = 10
log-queries-not-using-indexes  = off

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

```

Restart mysql after config file is updated

`/etc/init.d/mysql restart`