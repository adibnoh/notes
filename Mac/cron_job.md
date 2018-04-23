# Cron Job

## Edit Cron File using Nano

`env EDITOR=nano crontab -e`

## View Cron Tab

`crontab -l`

## Avoid Cron from sending mail to System

append this end of command

`>> /dev/null 2>&1`

example:

`* * * * * <your command> >/dev/null 2>&1`