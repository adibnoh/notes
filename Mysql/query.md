# Query

Common Queries for references

## Add Index

INDEX

```sql

ALTER TABLE `articles` ADD INDEX `date_publish_web` (`date_publish_web`)

```

FULLTEXT INDEX

```sql

ALTER TABLE `table` ADD FULLTEXT INDEX `column` (`column`)`

```

Refer:
## Reference

* [mysql too many index](https://stackoverflow.com/questions/4120160/mysql-too-many-indexes)