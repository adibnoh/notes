# Load Balancer

This is rough guide how to setup load balancer. This guide assume we setup our website using Laravel and Nginx or any PHP applications.

We need at least 2 server, one for load balancer and another for web server.

## Load Balancer Server

```

upstream backend {
    server 10.100.100.100:80;
}

server {
    ...


    location / {
        ...

        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header Host $http_host;
        proxy_set_header X-NginX-Proxy true;

        proxy_pass http://backend/;
        proxy_redirect off;
        
        ...
    }


    ...
}
```

## Web Server


```

server {
    ...

    location ~ \.php$ {
        ...

        # Override the load balancer IP with real IP.
        fastcgi_param REMOTE_ADDR $http_x_real_ip;

        ...
    }

    ...
}

```

[https://stackoverflow.com/a/60662195/24481404](https://stackoverflow.com/a/60662195/24481404)