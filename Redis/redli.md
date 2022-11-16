# Redli

Redli allow you to connect to Redis Database that require tls connection, such as Digital Ocean Redis Managed Database.

https://github.com/IBM-Cloud/redli

Go to release page, download `redli_*_darwin_amd64.tar.gz` binary. Extract the file then `chmod +x` the binary and move it to your path. For Mac OS, move to `/usr/local/bin/`

## Usage

`redli --tls -h <host> -a <password> -p <port>`

example:

`redli --tls -h redis.ondigitalocean.com -a PaSWoRD -p 25061`