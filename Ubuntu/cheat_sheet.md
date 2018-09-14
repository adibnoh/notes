# Cheat Sheet

## Login as root

Change to root when login as any user with root privileged

`sudo -i`

## List all hidden files and directory

`ls -a`

## List all file with filesize

`ls -lh`

## List all directories with directory size

`du -sh *`

## Delete oversize directory

Delete huge file count inside folder

`find <dir_path> -type f -delete`

or inside current directory

`find . -type f -delete`

## Report file system disk space usage

`df -h` - will show each first level directory

or

`df / -h` - will show total

## Get total storage of file or directory

`du -hs /path/to/directory`

## Rename/Move file or directory

`mv (option) filename1.ext filename2.ext`

## Copy file/directory

`cp <origin_path_to_file_or_directory> <destination_path_to_file_or_directory>`

## Empty file content

`> filename`

## Remove File

removes files beginning with `sequence_1` and ending with `.hmf`.

`rm sequence_1*.hmf`

remove all files and directory including hidden files in first directory level

`rm -rf {,.[!.],..?}*`

## Check Command Path

`whereis <command>`

or

`which <command>`

## Check Mime Type

`file --mime-type -b <filename>`

## Other packages

[https://pypi.python.org/pypi/Glances](https://pypi.python.org/pypi/Glances)

## Reference

* [https://askubuntu.com/questions/5444/how-to-find-out-how-much-disk-space-is-remaining](https://askubuntu.com/questions/5444/how-to-find-out-how-much-disk-space-is-remaining)
* [https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line](https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line)
* [https://unix.stackexchange.com/questions/37350/how-do-i-remove-multiple-files-with-a-common-prefix-and-suffix](https://unix.stackexchange.com/questions/37350/how-do-i-remove-multiple-files-with-a-common-prefix-and-suffix)