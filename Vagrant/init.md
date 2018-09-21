# Init

Install Virtual Box on Ubuntu

[https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)

Install vagrant on Ubuntu

`sudo apt-get install vagrant`

`sudo apt-get install virtualbox-dkms`

Cheat Sheet

`VBoxManage list vms`

`VBoxManage list runningvms`

`VBoxManage controlvm <uuid> poweroff`

`VBoxManage unregistervm <uuid>`

Setup Vagrant

[https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)

Init

`cd <desired directory>`

`vagrant init <vagrant boxes>` - eg: hashicorp/precise64 ,  https://atlas.hashicorp.com/boxes/search

Configure Vagrantfile

```conf

config.vm.box = “<vagrant boxes>"
config.vm.synced_folder “<local machine directory>", “<virtual machine directory>” - https://www.vagrantup.com/docs/synced-folders/basic_usage.html
config.vm.network :forwarded_port, guest: <virtual machine port>, host: <local machine port> - https://www.vagrantup.com/docs/networking/basic_usage.html

```

Run Vagrant

`vagrant up`

`vagrant reload` - reload vagrant configuration

Shutdown Vagrant

`vagrant halt`

Destroy Vagrant - this command is dangerous, use it with care. It will delete all app and configuration in virtual box

`vagrant destroy`

SSH to virtual machine

`vagrant ssh`

Change to root

`sudo su -`

Exit from virtual machine

Ctrl + D for ubuntu

Change ownership in sync folder - incase wordpress can’t modify in server

```conf

config.vm.synced_folder ".", "/var/www", :owner => 'www-data', :group => 'www-data'

```

mount: unknown filesystem type 'vboxsf'

```conf

config.vm.synced_folder '/home', '/home/vagrant', nfs: true

```

[https://github.com/virtuald/vagrant-rekey-ssh](https://github.com/virtuald/vagrant-rekey-ssh) - incase:  default: Warning: Authentication failure. Retrying… error occured

LAMP

`sudo apt-get update`

WARNING! Your environment specifies an invalid locale. This can affect your user experience significantly, including the ability to manage packages

`locale`

`export LANGUAGE=en_US.UTF-8; export LANG=en_US.UTF-8; export LC_ALL=en_US.UTF-8; locale-gen en_US.UTF-8`

`dpkg-reconfigure locales`

`reboot`

APACHE2

`sudo apt-get install apache2`

MARIA DB

`sudo apt-get install mariadb-server`

PHP 7

`sudo add-apt-repository ppa:ondrej/php`

`sudo apt-get update`

`sudo apt-get install php7.0`

`sudo apt-get install php7.0-mysql php7.0-cli php7.0-gd php7.0-json`

Restart Apache2

`sudo service apache2 reload`

[http://www.tecmint.com/install-php7-for-apache-nginx-on-ubuntu-14-04/](http://www.tecmint.com/install-php7-for-apache-nginx-on-ubuntu-14-04/)

[https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04)

[https://www.vultr.com/docs/install-mariadb-on-ubuntu-14-04](https://www.vultr.com/docs/install-mariadb-on-ubuntu-14-04)

[https://www.rosehosting.com/blog/how-to-reset-your-mariadb-root-password/](https://www.rosehosting.com/blog/how-to-reset-your-mariadb-root-password/)

If use nginx

Install nginx

`sudo apt-get install nginx`

Create the index file

`sudo nano /var/www/html/index.html`

```txt

Hello world

```

Save file and exit text editor by tying ctrl+x

Create nginx configuration file

`sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/<sitename>`

example

`sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/wordpress.boilerplate`

Configure nginx

`sudo nano /etc/nginx/sites-available/<sitename>`

example

`sudo nano /etc/nginx/sites-available/wordpress.boilerplate`

or

`sudo nano /etc/nginx/sites-available/adibnoh`

```conf

server {
        listen   80; ## listen for ipv4; this line is default and implied
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6

        root /var/www/example.com/public_html;
        index index.html index.htm;

        # Make site accessible from http://localhost/
        server_name example.com;
}
or
server {
        listen   <port_number> default_server; #edit this line
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6

        root /var/www/<your_dir>;
        index index.php index.html index.htm; ##edit this line

        # Make site accessible from http://localhost/
        server_name example.com;

       #for laravel replace this line
             location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                # try_files $uri $uri/ =404; #this line
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
                try_files $uri $uri/ /index.php$is_args$args; #with this line
        }

       #basic setup
      location ~ \.php$ {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
      }
}

```

for nginx 6666 port is not available by default

Create another config file inside sites-enabled directory, this file is sync with file inside sites-available directory

`sudo ln -s /etc/nginx/sites-available/test /etc/nginx/sites-enabled/test`

example

`sudo ln -s /etc/nginx/sites-available/wordpress.boilerplate /etc/nginx/sites-enabled/wordpress.boilerplate`

or

`sudo ln -s /etc/nginx/sites-available/jkns.gallery /etc/nginx/sites-enabled/jkns.gallery`

Restart nginx

`sudo service nginx restart`

Install Php Fpm

`sudo apt-get install php7.0-fpm`

`sudo apt-get install php7.0-mysql`

Install MariaDB

Restart MariaDB

`service mysql restart`

Laravel

`sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql`

`sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt`

`sudo apt-get install php5-gd` -> image plugin

`sudo service apache2 restart`

`sudo nano /etc/apache2/sites-available/000-default.conf` -> edit root file

`sudo service apache2 restart`

`curl -sS https://getcomposer.org/installer | php`

`sudo mv composer.phar /usr/local/bin/composer`

`mysql -u root -p -> access mysql`

`mysql > CREATE DATABASES <database name>;`

`cd <laravel folder>`

`php artisan migrate`

`php artisan db:seed`

`sudo a2enmod rewrite`

`sudo service apache2 restart`

Install php5-fpm

`sudo apt-get install php5-fpm`

Configure

`sudo nano /etc/php5/fpm/php.ini`

Find the line, cgi.fix_pathinfo=1, and change the 1 to 0.

```conf

cgi.fix_pathinfo=0

```

`sudo nano /etc/php5/fpm/pool.d/www.conf`

Find the line, listen = 127.0.0.1:9000, and change the 127.0.0.1:9000 to /var/run/php5-fpm.sock.

```conf

listen = /var/run/php5-fpm.sock


# also edit or uncomment
listen.owner = www-data
listen.group = www-data
listen.mode = 0660

```

Restart PHP

`sudo service php5-fpm restart`

`CHROME JS SYNTAXERROR: UNEXPECTED TOKEN ILLEGAL CAUSED BY VAGRANT SYNCED FOLDER`

[http://quyennt.com/web-development/chrome-js-syntaxerror-unexpected-token-illegal-caused-by-vagrant-synced-folder/](http://quyennt.com/web-development/chrome-js-syntaxerror-unexpected-token-illegal-caused-by-vagrant-synced-folder/)

if this problem occur, open nginx.conf

`sudo nano /etc/nginx/nginx.conf`

change sendfile on; to sendfile off;