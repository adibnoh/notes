# Snippet

Block access to certain file via file extension

```conf

location ~\.(ini|log|conf)$ {
     deny all;
     error_page 403 =404 / ;
 }

```