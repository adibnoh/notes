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

## List top 5 biggest size directories

`du -hs * | sort -rh | head -5`

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

remove hidden files and folder

`rm -R .*`

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

## Change file/folder Ownership

`sudo chown -R username:group directory`

## Delete log file

When your `/var/log` folder become to big, is good to cleanup once a while,

Delete all log

`find /var/log -type f -delete`

Delete all .gz and rotated file

`find /var/log -type f -regex ".*\.gz$"`

`find /var/log -type f -regex ".*\.[0-9]$"`

## Clear file content

`truncate -s 0 storage/logs/*log`

## List files in databases that match a pattern

`locate <program>`

## Reference

* [How to find out how much disk space is remaining?](https://askubuntu.com/questions/5444/how-to-find-out-how-much-disk-space-is-remaining)
* [How do I determine the total size of a directory (folder) from the command line?](https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line)
* [How do I remove multiple files with a common prefix and suffix?](https://unix.stackexchange.com/questions/37350/how-do-i-remove-multiple-files-with-a-common-prefix-and-suffix)
* [Delete all of Var Log](https://serverfault.com/questions/185253/delete-all-of-var-log)
* [Find Top Large Directories and Files Sizes in Linux](https://www.tecmint.com/find-top-large-directories-and-files-sizes-in-linux/)
* [How to truncate all logfiles?](https://askubuntu.com/questions/266738/how-to-truncate-all-logfiles#266740)