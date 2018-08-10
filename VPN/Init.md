# Init

Follow tutorial in reference section is enough just need to update this setting

`nano /home/<user_directory>/openvpn-ca/vars`

```conf

# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=$EASY_RSA/openssl-1.0.0.cnf #<-This format works

```

## Reference

* [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04)
* [https://ubuntuforums.org/showthread.php?t=2001055](https://ubuntuforums.org/showthread.php?t=2001055)