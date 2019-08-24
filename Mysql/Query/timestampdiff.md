# Timestampdiff

```sql

select * from hall where TIMESTAMPDIFF(MINUTE,open_date,close_date) > 1

```

## Sum TimeStampDiff in Group

```sql

SELECT t.user_id,
	SUM(
		TIMESTAMPDIFF(
			DAY,
			t.date_joined,
			IF(t.date_left is null, CURRENT_DATE, t.date_left)
		)
	) as yeardiff
    FROM members t
GROUP BY t.user_id

```

## Reference

* [Filtering table in MySQL with difference between two timestamp columns](https://stackoverflow.com/questions/39250006/filtering-table-in-mysql-with-difference-between-two-timestamp-columns)
* [Date and Time Functions](https://dev.mysql.com/doc/refman/5.7/en/date-and-time-functions.html)
* [MySQL: How to SUM() a TIMEDIFF() on a group?](https://stackoverflow.com/questions/4102480/mysql-how-to-sum-a-timediff-on-a-group)