# Duplicate


Get duplicate records based on multiple column, except latest duplicate based on biggest primary key

```sql

select * from posts
where id not in 
(
	select max(id)
	from posts
	group by title, headline, body
)

```

Delete duplicate records, except latest duplicate based on biggest primary key

```sql

delete from posts
where id not in 
(
	select * from (
		select max(id)
		from posts
		group by title, headline, body
	) as c
) 

```