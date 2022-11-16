# DBngin

## Mysqldump

We need to ensure we've already export env variable to terminal, then we can get mysqldump path by running this command `which mysqldump`

## Socket

DBngin use custom socket for each database instance.

`/tmp/<db_type>_<port>.sock`

eg:

`/tmp/mysql_3306.sock`

## Reference

* [https://github.com/TablePlus/DBngin/issues/52#issuecomment-700144597](https://github.com/TablePlus/DBngin/issues/52#issuecomment-700144597)

