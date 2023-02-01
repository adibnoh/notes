# Cheat Sheet

## Change to root

`sudo -i`

## CloudFlare

`Let's Encrypt SSL Too Many Redirects`

[Let's Encrypt SSL Too Many Redirects](https://laracasts.com/discuss/channels/forge/lets-encrypt-ssl-too-many-redirects)

## Recipes

Most of these recipes need to be tested

### Install locale

```
# You should change fr_CA for the locale you want.
echo ">> Installing fr_CA locale"
sudo locale-gen fr_CA
sudo locale-gen fr_CA.UTF-8
```

[https://forgerecipes.com/recipes/83](https://forgerecipes.com/recipes/83)

### Install htop

```
sudo apt-get install htop
```

https://forgerecipes.com/recipes/141

### Install Digital Ocean Monitoring Tools

```
#!/usr/bin/env bash

curl -sSL https://agent.digitalocean.com/install.sh | sh
```

https://forgerecipes.com/recipes/174

### Disable MySQL8 Binary Logs

```
# Disable MySQL8 Binary Logs
echo "disable_log_bin" >> /etc/mysql/my.cnf

# Restart MySQL
service mysql restart

# To manually clear existing logs
# ssh forge@serverip
# mysql -u root -p
# <enter forge Database Password>
# RESET MASTER;
# exit;
```

https://forgerecipes.com/recipes/229

### Spatie Image Optimizer Optimizers installation

```
sudo apt-get install jpegoptim
sudo apt-get install optipng
sudo apt-get install pngquant
sudo npm install -g svgo@1.3.2
sudo apt-get install gifsicle
sudo apt-get install webp
```