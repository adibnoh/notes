# Caffeinate

Prevent mac from sleeping

## NAME
     caffeinate -- prevent the system from sleeping on behalf of a utility

## SYNOPSIS
     caffeinate [-disu] [-t timeout] [-w pid] [utility arguments...]

## DESCRIPTION
     caffeinate creates assertions to alter system sleep behavior.  If no
     assertion flags are specified, caffeinate creates an assertion to prevent
     idle sleep.  If a utility is specified, caffeinate creates the assertions
     on the utility's behalf, and those assertions will persist for the dura-
     tion of the utility's execution. Otherwise, caffeinate creates the asser-
     tions directly, and those assertions will persist until caffeinate exits.

     Available options:

     -d      Create an assertion to prevent the display from sleeping.

     -i      Create an assertion to prevent the system from idle sleeping.

     -m      Create an assertion to prevent the disk from idle sleeping.

     -s      Create an assertion to prevent the system from sleeping. This
             assertion is valid only when system is running on AC power.

     -u      Create an assertion to declare that user is active. If the dis-
             play is off, this option turns the display on and prevents the
             display from going into idle sleep. If a timeout is not specified


## Usage

`caffeinate -disum`