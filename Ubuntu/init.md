# Init

After virtual server already created, you need to create new user to access the server remotely before run anything else.

## Login to server as root

`ssh root@<server_ip_address>`

## Create New User

`adduser <username>`

## Add user to a sudo group

`usermod -aG sudo <username>`

## Root Priviledge (if previous command dont work)

`gpasswd -a <username> sudo`

## Setup remote access for new user

### Login as new user

`su - <username>`

### Add your public key to authorized key

`mkdir .ssh`

`chmod 700 .ssh`

`nano .ssh/authorized_keys`

`Paste your public key in authorized_keys`

`chmod 600 .ssh/authorized_keys`

### Disallow root remote login

`Login back to server as root`

### Edit sshd_config

`nano /etc/ssh/sshd_config`

### Change this part

`PermitRootLogin no`

## Restart ssh

`service ssh restart`

## Update OS

Listing possible update

`sudo apt-get update`

Listing possible update and install update

`sudo apt-get update && sudo apt-get dist-upgrade`

Clean and remove old and unused package

* `apt-get clean` → cleans the packages and install script in /var/cache/apt/archives/
* `apt-get autoclean` → cleans obsolete deb-packages, less than clean
* `apt-get autoremove` → removes orphaned packages which are not longer needed from the system, but not purges them, use the --purge option together with the command for that.

## Reference

* [https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04)
* [https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart](https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart)
* [https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)
* [https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users](https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users)