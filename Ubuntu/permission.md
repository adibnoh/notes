# Permission

`chmod [-R] u=rwx,g=rw,o=r /path`

`chmod` - command use to change permission

`-R` - recursive flag

`u=rwx,g=rw,o=r` - can be break down to 3 part

* `u=rwx` - `u` refer to users; here we give permission to read, write and execute
* `g=rw` - `g` refer to groups; here we give permission to read and write only
* `o=r` - `o` refer to other; here we give permission to read only

## Read

Read is the ability to read the contents of a file, including open in an editor in a read-only format

## Write

Write is the ability to modify or delete a file

## Execute

Execute is the ability to run the file as a program (e.g. a shell script, python script, php script)