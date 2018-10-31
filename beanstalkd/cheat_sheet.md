# Cheat Sheet

By default beanstalk comes up on port 11300 so you can greet it by telnetting to there:

`telnet localhost 11300`

How is your beanstalkd feeling today? You can ask it by typing stats - this gives quite a lot of output but will include how many jobs are waiting/in progress/failed. In fact from this telnet prompt you can look at a bunch of things; here's a handful of my favorites commands:

* list-tubes - shows which tubes are available/in use
* use-tube [tube] - use a specific tube
* stats-tube [tube] - get the stats for a single tube
* peek-ready - shows the next job to be processed in the current tube

## Reference

[Getting Started with Beanstalkd](https://lornajane.net/posts/2014/getting-started-with-beanstalkd)