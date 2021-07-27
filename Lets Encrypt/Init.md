# Init

## Install

`sudo add-apt-repository ppa:certbot/certbot`

`sudo apt-get update`

`sudo apt-get install python-certbot-nginx`

## Update firewall

`sudo ufw allow 'Nginx Full'`

`sudo ufw delete allow 'Nginx HTTP'`

## Get SSL Cert

ensure web directory is same as domain name

`sudo certbot --nginx -d domain.com`

### Web Root Path Method

You may try this method too.

`certbot certonly --webroot --webroot-path <public_path_to_domain> --renew-by-default -d yourdomainhere.com`

if you want to add more subdomain just append `-d <domain>` to command above, eg:

`certbot certonly --webroot --webroot-path <public_path_to_domain> --renew-by-default -d example.com -d dev.example.com`

After that you need to manually add this line to your nginx config

```conf

...

server {
    ...

    listen 443 ssl;
    ssl_certificate /etc/letsencrypt/live/<yourdomainhere.com>/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/<yourdomainhere.com>/privkey.pem;
    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;


    if ($scheme != "https") {
        return 301 https://$host$request_uri;
    }

    ...
}

...

```

After that restart your nginx server

### Nginx Method

`sudo certbot --nginx -d example.com -d www.example.com`

## Test renewal process

`sudo certbot renew --dry-run`

If after Test renewal process show any error and cannot restart nginx follow this [fix][#after-install-cannot-reload-nginx]

## Check Status

`sudo certbot certificates`

## Issue

### Cannot Authenticated

```log
Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA
```

`sudo certbot --authenticator standalone --installer nginx --pre-hook "service nginx stop" --post-hook "fuser -k 443/tcp; service nginx start"`

### After install cannot reload Nginx

```log
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] bind() to 0.0.0.0:443 failed (98: Address already in use)
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] bind() to 0.0.0.0:5501 failed (98: Address already in use)
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] bind() to [::]:5501 failed (98: Address already in use)
Jan 31 11:23:56 for-the-win nginx[31506]: nginx: [emerg] still could not bind()
Jan 31 11:23:56 for-the-win systemd[1]: nginx.service: Control process exited, code=exited status=1
Jan 31 11:23:56 for-the-win systemd[1]: Failed to start A high performance web server and a reverse proxy server.
Jan 31 11:23:56 for-the-win systemd[1]: nginx.service: Unit entered failed state.
Jan 31 11:23:56 for-the-win systemd[1]: nginx.service: Failed with result 'exit-code'.
```

Solution

`sudo fuser -k 443/tcp`

`service nginx restart`

## Refer

* [https://www.digitalocean.com/community/questions/nginx-is-unable-to-bind-to-443](https://www.digitalocean.com/community/questions/nginx-is-unable-to-bind-to-443)
* [https://github.com/certbot/certbot/issues/5405](https://github.com/certbot/certbot/issues/5405)
* [https://gist.github.com/harryfinn/e36e41cdbfba5a6e1d69d6498a4fc5ee](https://gist.github.com/harryfinn/e36e41cdbfba5a6e1d69d6498a4fc5ee)