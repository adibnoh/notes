# Install Lets Encrypt on Ubuntu 20.04 + Nginx

## Install Lets Encrypt

`sudo apt install certbot python3-certbot-nginx`

## Allow Nginx Full Profile

`sudo ufw allow 'Nginx Full'`

`sudo ufw delete allow 'Nginx HTTP'`

## Usage

### Check your Nginx Config

Ensure the config is like this, all ssl configuration will be added by cert bot

```conf

server {                                                              
        listen 80;                                                    
        listen [::]:80;                                               
                                                                      
        root /home/<user>/domain.com;                              
        index index.php index.html index.htm index.nginx-debian.html; 
                                                                      
        server_name domain.com;                                 
                                                                      
        access_log off;                                               
        error_log  /var/log/nginx/domain.com-error.log error;   
                                                                      
        location / {                                                  
                # First attempt to serve request as file, then        
                # as directory, then fall back to displaying a 404.   
                # try_files $uri $uri/ =404;                          
                try_files $uri $uri/ /index.php?$query_string;        
        }                                                             
                                                                      
        location ~ \.php$ {                                           
                include snippets/fastcgi-php.conf;                    
                fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;       
        }                                                             
}                                                                     
                                                                      

```

`sudo certbot --nginx -d example.com`

## Verify

`sudo systemctl status certbot.timer`

`sudo certbot renew --dry-run`

## Remark

Always refer to original documentation, this document only for quick reference only

## References

* [How To Secure Nginx with Let's Encrypt on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04)