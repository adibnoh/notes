# Cron Job

## Edit Cron File using Nano

`env EDITOR=nano crontab -e`

## View Cron Tab

`crontab -l`

## Enable logging

append this end of command

`>  <path_to_log_file>`

example

`* * * * * <your command> > /User/John/log.txt`