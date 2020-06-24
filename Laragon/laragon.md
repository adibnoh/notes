# Laragon

## Install php 7.4.*

`menu -> php -> version -> click how to add another php version`

it will bring you to laragon forum, but you directly can go to https://windows.php.net/download

choose your desired php version, and download "zip link"

![](https://i.imgur.com/FY3yRRE.png)

unzip zip file you just downloaded. move extracted content inside "php directory".

you can get the directory from `menu -> php -> version -> dir ...` or it usually reside here `C:\laragon\bin\php`

restart laragon.

`menu -> php -> version -> choose your desired php packages`

## Install mysql

`menu -> mysql -> version -> click how to add another mysql version`

it will bring you to laragon forum, but you directly can go to https://dev.mysql.com/downloads/installer/ , you can search previous mysql version by clicking "looking for previous mysql version" link

![](https://i.imgur.com/06HdpeR.png)

unzip zip file you just downloaded. move extracted content inside "mysql directory".

you can get the directory from `menu -> mysql -> version -> dir ...` or it usually reside here `C:\laragon\bin\mysql`

restart laragon.

`menu -> mysql -> version -> choose your desired mysql packages`

### Mysql 8.*

forgot how i managed to do it, but you need to enter mysql via terminal and set root password there, if you cannot access mysql as usual via heidisql, please refer reference at the bottom

## Using nginx instead of apache

`menu -> preference -> services & ports -> untick apache checkbox and tick nginx checkbox`

## Enabled nginx ssl

`menu -> preference -> services & ports -> tick checkbox nginx enable ssl`

## Enable ssl for preferred site

`menu -> nginx -> sites enabled -> click your desired site to enabled ssl`

once added, u can access the site via https://<domain_name>:8443

## Reference

* [https://forum.laragon.org/topic/1766/laragon-4-0-16-mysql-8-0-18-mysql-cannot-start/3](https://forum.laragon.org/topic/1766/laragon-4-0-16-mysql-8-0-18-mysql-cannot-start/3)

