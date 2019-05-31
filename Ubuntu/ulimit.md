# Ulimit

Ulimit is the number of open file descriptors per process. It is a method for restricting the number of various resources a process can consume. Sometimes you will get the error message is like “too many files open “, it is because you have reached the limits of opened files, so you need to increase the ulimit parameters.

## Hard Limit

It is the maximum allowed limit to a user and this is set by the root user.

`ulimit -Hn` - will check current hard limit set by root

`su <user> --shell /bin/bash --command "ulimit -Hn"` - will check current hard limit for specific user

### Change Hard Limit

`nano /etc/security/limits.conf`

add this line at the end of file

`<user> hard nofile <hard_limit>`

eg:

`joe hard nofile 9000` - we are setting max hard limit for user joe to 9000

## Soft Limit

It is the effective value right now for that user. The user can change this limit, but we cannot set the soft limit higher than the hard limit.

`ulimit -Hn` - will check current soft limit set by root

`su <user> --shell /bin/bash --command "ulimit -Sn"` - will check current hard limit for specific user

### Change Soft Limit

`nano /etc/security/limits.conf`

add this line at the end of file

`<user> soft nofile <hard_limit>`

eg:

`joe soft nofile 9000` - we are setting max hard limit for user joe to 9000

## Reference

* [What is Ulimit Parameter? How to manage it?
](https://www.interserver.net/tips/kb/ulimit-parameter-manage/)
* [Find ulimit -a for other users](https://stackoverflow.com/questions/25302890/find-ulimit-a-for-other-users/34400864)
