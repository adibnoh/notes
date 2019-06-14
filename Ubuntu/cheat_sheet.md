# Cheat Sheet

## Login as root

Change to root when login as any user with root privileged

`sudo -i`

## List all users

`cat /etc/passwd`

## Report file system disk space usage

`df -h` - will show each first level directory

or

`df / -h` - will show total

## Check Command Path

`whereis <command>`

or

`which <command>`

## Check Mime Type

`file --mime-type -b <filename>`

## Other packages

[Glances](https://pypi.python.org/pypi/Glances)

## Change file/folder Ownership

`sudo chown -R username:group directory`

## Delete log file

When your `/var/log` folder become to big, is good to cleanup once a while,

Delete all log

`find /var/log -type f -delete`

Delete all .gz and rotated file

`find /var/log -type f -regex ".*\.gz$"`

`find /var/log -type f -regex ".*\.[0-9]$"`

## Reference

* [How to find out how much disk space is remaining?](https://askubuntu.com/questions/5444/how-to-find-out-how-much-disk-space-is-remaining)
* [How do I determine the total size of a directory (folder) from the command line?](https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line)
* [How do I remove multiple files with a common prefix and suffix?](https://unix.stackexchange.com/questions/37350/how-do-i-remove-multiple-files-with-a-common-prefix-and-suffix)
* [Delete all of Var Log](https://serverfault.com/questions/185253/delete-all-of-var-log)
* [Find Top Large Directories and Files Sizes in Linux](https://www.tecmint.com/find-top-large-directories-and-files-sizes-in-linux/)
* [How to truncate all logfiles?](https://askubuntu.com/questions/266738/how-to-truncate-all-logfiles#266740)
* [Linux List All Users In The System](https://www.cyberciti.biz/faq/linux-list-users-command/)