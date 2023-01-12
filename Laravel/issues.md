# Issues

## count Slow

This can be seen when your query is using pagination.

pagination is slow because it count result for pagination. It will be much worse if inside your query contain whereHas. This is because whereHas is subQuery, and subQuery is slow by nature.

## whereHas Slow

need to replace with join instead

## Mysql Date Slow

* [MySQL performance problem using indexed datetime column](https://dba.stackexchange.com/questions/73598/mysql-performance-problem-using-indexed-datetime-column)
* [DATE() MONTH() etc. functions slow down query](https://stackoverflow.com/questions/37777883/date-month-etc-functions-slow-down-query/37777987)

