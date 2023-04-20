# Partition

We're using range by year partition.

## Create table with partition

```sql

CREATE TABLE employees (
    id INT NOT NULL,
    fname VARCHAR(30),
    lname VARCHAR(30),
    hired DATE NOT NULL DEFAULT '1970-01-01',
    separated DATE NOT NULL DEFAULT '9999-12-31',
    job_code INT,
    store_id INT
)
PARTITION BY RANGE ( YEAR(separated) ) (
    PARTITION p0 VALUES LESS THAN (1991),
    PARTITION p1 VALUES LESS THAN (1996),
    PARTITION p2 VALUES LESS THAN (2001),
    PARTITION p3 VALUES LESS THAN MAXVALUE
);

```

## Alter partition on existing table

```sql

alter table employees PARTITION by range ( year(separated)) (
	PARTITION p0 VALUES LESS THAN (1991),
    PARTITION p1 VALUES LESS THAN (1996),
    PARTITION p2 VALUES LESS THAN (2001),
        PARTITION p3 VALUES LESS THAN (2005),
    PARTITION pMax VALUES LESS THAN MAXVALUE
)

```

this will overwrite any previous partition

## Add new partition

```sql

ALTER TABLE table_name ADD PARTITION (partition_definition);

```

## Remove partition

```sql

ALTER TABLE table_name DROP PARTITION partition_name;

```

## Merge partition

```sql

ALTER TABLE table_name COALESCE PARTITION partition_name;

```

## Split partition

```sql

ALTER TABLE table_name REORGANIZE PARTITION partition_name INTO (partition_definition, partition_definition, ...);

```

example

```sql

ALTER TABLE views REORGANIZE PARTITION future INTO (
    PARTITION year2024 VALUES LESS THAN (2024), 
    PARTITION future VALUES LESS THAN MAXVALUE
);

```

https://github.com/lucabecchetti/laravel-mysql-partition/issues/1#issuecomment-1208883016

## View partition info

```sql

SHOW CREATE TABLE table_name;

```

```sql

SELECT * FROM INFORMATION_SCHEMA.PARTITIONS WHERE TABLE_NAME = 'table_name';

```