# Issues

## Too many sleep connection that are old

This might occur when user open connection to database but never made a query.

By default mysql leave open connection for 28,800 (8 hours) long. To change this setting add this line inside `my.cnf`

```

[mysqld]
interactive_timeout=180
wait_timeout=180

```
