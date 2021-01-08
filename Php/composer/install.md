# Install

## Install Globally on Ubuntu Server

Anywhere in your server run this command below

`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`

`php -r "if (hash_file('sha384', 'composer-setup.php') === 'e5325b19b381bfd88ce90a5ddb7823406b2a38cff6bb704b0acc289a09c8128d4a8ce2bbafcd1fcbdc38666422fe2806') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`

This command below will install composer globally

`sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer`

Please always refer original documentation, before refering to this documents

* [Download Composer](https://getcomposer.org/download/)
* [How To Install and Use Composer on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04)