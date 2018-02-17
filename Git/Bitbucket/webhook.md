# Webhook

## Create SSH Key

Create an ssh directory for the Nginx

`sudo mkdir /var/www/.ssh`

`sudo chown -R www-data:www-data /var/www/.ssh/`

Generate a deploy key for Nginx

`sudo -Hu www-data ssh-keygen -t rsa # choose "no passphrase"`

`sudo cat /var/www/.ssh/id_rsa.pub`

Add ssh key to deployment key in bitbucket.

## Sample file

```php

<?php

    include('config.php');

    if ($_REQUEST['key'] == $secret_key)
    {

        $output = shell_exec('cd ' . $git_dir . ' && git pull origin master 2>&1');
        $status = shell_exec('cd ' . $git_dir . ' && git rev-parse --short HEAD 2>&1');

        //Log the request and result
        file_put_contents('webhook.log', "\n$output\nCurrent hash is $status\n################################################\n", FILE_APPEND);

        echo "has request";

    } else {

        echo "no request";
        file_put_contents('webhook.log', "Unknown request at:".date('ymdhis')."\n################################################\n", FILE_APPEND);

    }

```