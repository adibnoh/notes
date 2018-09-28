# Lamp

Lamp stand for Linux, Apache, Mysql and Php

[https://www.atlantic.net/community/howto/install-lamp-centos-6/](https://www.atlantic.net/community/howto/install-lamp-centos-6/)

## Apache

Install Apache

`sudo yum install httpd`

Start Server

`sudo service httpd start`

## Php

[https://www.mojowill.com/geek/howto-install-php-5-4-5-5-or-5-6-on-centos-6-and-centos-7/](https://www.mojowill.com/geek/howto-install-php-5-4-5-5-or-5-6-on-centos-6-and-centos-7/)

Check Php package

`php -m`

Install MB String extension

`yum install php-mbstring`

If exist conflict

[http://stackoverflow.com/questions/31580464/php-installation-conflicts-on-centos6](http://stackoverflow.com/questions/31580464/php-installation-conflicts-on-centos6)

install ext dom , restart server afterward, [http://smartwebdeveloper.com/centos/install-the-php-dom-extension-on-centos](http://smartwebdeveloper.com/centos/install-the-php-dom-extension-on-centos)

`sudo yum install php-xml`

## Mysql

Use any below link, skip configure phpmyadmin.conf, those setup will allow only single ip gain access to phpmyadmin

* [http://www.liquidweb.com/kb/how-to-install-and-configure-phpmyadmin-on-centos-6](http://www.liquidweb.com/kb/how-to-install-and-configure-phpmyadmin-on-centos-6)
* [https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-a-centos-6-4-vps](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-a-centos-6-4-vps)

Install Mysql

`sudo yum install mysql-server`

Start Mysql

`sudo service mysqld start`

Set Mysql root password, set yes to everything

`/usr/bin/mysql_secure_installation`

Optional - run httpd and mysql everytime server start

`sudo chkconfig httpd on`

`sudo chkconfig mysqld on`

## PhpMyAdmin

[http://ask.xmodulo.com/install-phpmyadmin-centos.html](http://ask.xmodulo.com/install-phpmyadmin-centos.html)

Follow this link instead, granted all url to phpmyadmin, skip blowfish part.

Add EPEL repo

`rpm -iUvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm`

Install PhpMyAdmin

`yum -y install phpmyadmin`

Configure PhpMyAdmin

`nano /etc/httpd/conf.d/phpMyAdmin.conf`

```conf
<Directory /usr/share/phpMyAdmin/>
   AddDefaultCharset UTF-8

   <IfModule mod_authz_core.c>
     # Apache 2.4
     <RequireAny>
       #Require ip 127.0.0.1
       #Require ip ::1
       Require all granted
     </RequireAny>
   </IfModule>
   <IfModule !mod_authz_core.c>
     # Apache 2.2
     Order Deny,Allow
     #Deny from All
     Allow from 0.0.0.0
     #Allow from ::1
   </IfModule>
</Directory>

<Directory /usr/share/phpMyAdmin/setup/>
   <IfModule mod_authz_core.c>
     # Apache 2.4
     <RequireAny>
       #Require ip 127.0.0.1
       #Require ip ::1
       Require all granted
     </RequireAny>
   </IfModule>
   <IfModule !mod_authz_core.c>
     # Apache 2.2
     Order Deny,Allow
     #Deny from All
     Allow from 0.0.0.0
     #Allow from ::1
   </IfModule>
</Directory>

```