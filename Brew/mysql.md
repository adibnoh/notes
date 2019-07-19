# Mysql

## Cannot connect to Mysql after brew cleanup

run `mysql` at terminal will show this message

```txt
mysql: Can't read dir of '/usr/local/etc/my.cnf.d' (Errcode: 2 - No such file or directory)
mysql: [ERROR] Fatal error in defaults handling. Program aborted!
```

Solution

`mkdir /usr/local/etc/my.cnf.d`