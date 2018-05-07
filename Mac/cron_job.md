# Cron Job

## Edit Cron File using Nano

`env EDITOR=nano crontab -e`

## View Cron Tab

`crontab -l`

## Avoid Cron from sending mail to System

append this end of command

`>/dev/null 2>&1`

`>` is for redirect

`/dev/null` is a black hole where any data sent, will be discarded

`2` is the file descriptor for Standard Error

`>` is for redirect

`&` is the symbol for file descriptor (without it, the following 1 would be considered a filename)

`1` is the file descriptor for Standard Out

Therefore `>/dev/null 2>&1` is redirect the output of your program to `/dev/null`. Include both the Standard Error and Standard Out.

cron will only email you if there is some output from your job. With everything redirected to null, there is no output and hence cron will not email you.

example:

`* * * * * <your command> >/dev/null 2>&1`

## Enable logging

append this end of command

`>  <path_to_log_file>`

example

`* * * * * <your command> > /User/John/log.txt`