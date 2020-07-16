# Session duration based on entry log

Table: entries
+--------------+---------------------+-----------------+
| user_id      | created_at          | event           |
+--------------+---------------------+-----------------+
|            1 | 2011-08-16 09:53:29 | login           |
|            1 | 2011-08-16 10:45:42 | logout          |
|            1 | 2011-08-16 10:55:29 | login           |
|            1 | 2011-08-16 17:55:39 | logout          |
+--------------+---------------------+-----------------+


```sql


SELECT
    user_id,
    TIME_FORMAT(SEC_TO_TIME(    
        IF(SUM(TIME) < 0, 
            SUM(TIME) + TO_SECONDS(NOW()), 
            IF(SUM(TIME) > 63000000000, SUM(TIME) - TO_SECONDS(NOW()), SUM(TIME))
        )
    ),'%Hh %im') AS TOTAL_TIME
FROM
(
    SELECT 
        TO_SECONDS(c.created_at) * - 1 AS TIME, c.socket_id
    FROM entries c
    WHERE event = 'open'
    UNION
    SELECT 
        TO_SECONDS(created_at) AS TIME, user_id  
    FROM entries
    WHERE event = 'close'
) t
GROUP BY user_id WITH ROLLUP
;

```

## Reference

* [http://sqlfiddle.com/#!9/85650/2](http://sqlfiddle.com/#!9/85650/2)
* [https://stackoverflow.com/questions/19852868/mysql-query-for-total-online-time-based-on-login-logout-entries](https://stackoverflow.com/questions/19852868/mysql-query-for-total-online-time-based-on-login-logout-entries)