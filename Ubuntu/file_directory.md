# File and Directory

## List all hidden files and directory

`ls -a`

## List all file with filesize

`ls -lh`

## List all directories with directory size

`du -sh *`

## List top 5 biggest size directories

`du -hs * | sort -rh | head -5`

## Find file by filename

`find <location> -iname "filename"`

Leave empty if want to search current_directory recursively

eg:

`find -iname "photo.jpg"`

## Delete oversize directory

Delete huge file count inside folder

`find <dir_path> -type f -delete`

or inside current directory

`find . -type f -delete`

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

## Clear file content

`truncate -s 0 storage/logs/*log`

## List files in databases that match a pattern

`locate <program>`