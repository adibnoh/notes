# Optimise

## Config

### Static File Caching

```conf

server {

    location ~* .(jpg|jpeg|png|gif|ico|css|js)$ {
        expires 365d;
    }

}


```

## References

* [](https://www.digitalocean.com/community/tutorials/how-to-optimize-nginx-configuration)