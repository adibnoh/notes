# Query

Common Queries for references

## Add Index

INDEX

```sql

ALTER TABLE `articles` ADD INDEX `date_publish_web` (`date_publish_web`)

```

FULLTEXT INDEX

```sql

ALTER TABLE `table` ADD FULLTEXT INDEX `<index_name>` (`column`)`

```

## Alter Column

```sql

ALTER TABLE mytable CHANGE `time` `time` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP

```

## Count Union

```sql

select count(*)
as aggregate from
(
  (
    select id, title, updated_at, "topic" as type from `topics` where `title` LIKE '%they%'
  )
  union
  (
    select id, subtopics_title as title, updated_at, "subtopic" as type
    from `subtopics` where `subtopics_title` LIKE '%they%'
  )
) as `temp_table`

```

## Having

One of `Having` purpose is to filter `GROUP BY` clause

```sql

...
GROUP BY meetingID
HAVING COUNT( caseID )<4


```

`Having` with multiple condition

```sql

...
GROUP BY meetingID
HAVING COUNT(caseID) < 4 AND COUNT(caseID) > 2

```

## Reference

* [mysql too many index](https://stackoverflow.com/questions/4120160/mysql-too-many-indexes)
* [Multiple aggregate functions in HAVING clause](https://stackoverflow.com/questions/14756222/multiple-aggregate-functions-in-having-clause)