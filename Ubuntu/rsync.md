# Rsync

## Copy files/folder from remote to local

`rsync -auzv -e ssh <username>@<ip_address>:<origin_path> <destination_path>`

example - copy folder blog to folder adibnoh.

`rsync -auzv -e ssh adibnoh@168.283.192.193:/home/adibnoh/blog /home/adibnoh`

## Ignore folder

`rsync -auzv --exclude 'dir1' source/ destination/`

## References

* [https://kyup.com/tutorials/copy-files-rsync-ssh/](https://kyup.com/tutorials/copy-files-rsync-ssh/)