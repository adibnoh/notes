# Lets Encrypt - Init

## Install

`sudo add-apt-repository ppa:certbot/certbot`

`sudo apt-get update`

`sudo apt-get install python-certbot-nginx`

## Update firewall

`sudo ufw allow 'Nginx Full'`

`sudo ufw delete allow 'Nginx HTTP'`

## Get SSL Cert

`sudo certbot --nginx -d example.com -d www.example.com`

## Test renewal process

`sudo certbot renew --dry-run`

If after Test renewal process show any error and cannot restart nginx follow this [fix][#after-install-cannot-reload-nginx]

## Issue

### 

```
Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA
```

`sudo certbot --authenticator standalone --installer nginx --pre-hook "service nginx stop" --post-hook "fuser -k 443/tcp; service nginx start"`

### After install cannot reload Nginx

```
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

https://www.digitalocean.com/community/questions/nginx-is-unable-to-bind-to-443

https://github.com/certbot/certbot/issues/5405