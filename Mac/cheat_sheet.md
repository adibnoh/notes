# Cheat Sheet

## Create random string

`openssl rand -base64 6`

or

`openssl rand -hex 13`

## Copy content of file to clipboard

`pbcopy < file`

## CSV

Split csv per line

`split -l <line_number_to_split> <file_path>`

example:

`split -l 200 split_me`

## Create Custom Alias

Go to home directory

`cd ~`

Create/Edit bash profile file

`nano .bash_profile`

Add alias in a new line

`alias l='ls -lah'`

Reload bash profile

`source ~/.bash_profile`

## Reference

* [Generate Random Passwords Command Line](http://osxdaily.com/2011/05/10/generate-random-passwords-command-line/)
* [Make an alias in bash shell in OSX terminal](https://coolestguidesontheplanet.com/make-an-alias-in-bash-shell-in-os-x-terminal/)