# SSL

SSL connection may not work while accessing site under homestead, to resolve this we need to install homestead certificate to our browser

1. SSH to homestead
2. cd /etc/nginx/ssl
3. cp ca.homestead.homestead.crt /home/vagrant/<homestead_shared_directory>

You should see `ca.homestead.homestead.crt` file inside your <homestead_shared_directory>, we need to import `ca.homestead.homestead.crt` to our browser

## Import certificate to Chrome

open chrome settings by opening this url in chrome browser `chrome://settings`

navigate to Security -> Manage Certificates -> Trusted Root Certificates Authorities

then click button `import`, it should self-explainatory from there.

restart chrome

## Import certificate to Firefox

open firefox privacy settings by opening this url in firefox browser `about:preferences#privacy`

navigate to Security -> Certificates -> View Ceritificates -> Authorities

then click button `import`, it should self-explainatory from there.

restart firefox

## Reference

[SSL Certificates with Laravel Homestead on Windows (HTTPS)](https://medium.com/dinssa/ssl-certificates-laravel-homestead-windows-https-f83ec8b3198)