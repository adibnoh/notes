# SCP

SCP is a program in linux that allow us to copy file across filesystem

## Copy file from server to local

`scp username@hostname:/path/to/remote/file /path/to/local/file`

## Copy file from server to server

`scp username1@hostname1:/path/to/file username2@hostname2:/path/to/other/file`

## Copy file from local to server

`scp /path/to/local/file username@hostname:/path/to/remote/file`