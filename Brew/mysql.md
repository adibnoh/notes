# Mysql

Currently most common version is Mysql 8.0 (latest one) and Mysql 5.7.

## Installation and Usage

### 8.0

`brew install mysql` - will install latest mysql version.

`brew link mysql` - link brew with mysql.

`brew services start mysql` - start mysql.

### 5.7

`brew install mysql@5.7` - will install mysql version 5.7. Current latest version for 5.7 is 5.7.27.

`brew link mysql@5.7`

`brew services start mysql@5.7`

### Change between version

To change between mysql version we need to stop running current mysql service and unlink from brew.

After that start mysql services with our desired version and link that mysql to brew.

eg (change from Mysql 8.0 to 5.7)

`brew services stop mysql`

`brew unlink mysql`

`brew services start mysql@5.7`

`brew link mysql@5.7`

## List all possible config location

`mysql --help | grep cnf`

## Cannot connect to Mysql after brew cleanup

run `mysql` at terminal will show this message

```txt
mysql: Can't read dir of '/usr/local/etc/my.cnf.d' (Errcode: 2 - No such file or directory)
mysql: [ERROR] Fatal error in defaults handling. Program aborted!
```

Solution

`mkdir /usr/local/etc/my.cnf.d`

## Cannot connect through localhost

This is issue encounter with mysql 8.0, the solution is we need to setup root password and allow localhost access to mysql.

1. Locate your `my.cnf` file. `locate my.cnf`. Usually located at `/usr/local/etc/my.cnf`.
2. Edit `my.cnf` file

```cnf

default-authentication-plugin=mysql_native_password

```

3. Login to mysql via terminal. `mysql -uroot` or `mysql -uroot -p` (if existing config has password).
4. Run this query

```sql

-- Replace [password] with your own password
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '[password]';

```

5. Exit mysql shell.
6. Restart mysql. `brew services restart mysql`

[Sequel Pro and MySQL connection failed](https://stackoverflow.com/questions/51179516/sequel-pro-and-mysql-connection-failed)

## Cannot connect through socket

This is issue encounter with Mysql 5.7.

Error message - `ERROR 2002 (HY000): Can’t connect to local MySQL server through socket ‘/tmp/mysql.sock’ (2)`

Need to reinstall Mysql and remove certain directory.

`brew uninstall mysql@5.7`

`rm -rf /usr/local/var/mysql`

`rm /usr/local/etc/my.cnf`

`brew install mysql@5.7`

`brew link --force mysql@5.7`

`brew services start mysql@5.7`

[brew install mysql@5.7 can't connect to local MySQL server through socket](https://superuser.com/questions/1333504/brew-install-mysql5-7-cant-connect-to-local-mysql-server-through-socket)