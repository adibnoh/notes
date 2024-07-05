# Access Type

Note taken from [https://planetscale.com/learn/courses/mysql-for-developers/queries/explain-access-types](https://planetscale.com/learn/courses/mysql-for-developers/queries/explain-access-types)

## Understanding MySQL's EXPLAIN access method types

The `EXPLAIN` function allows you to see how MySQL executes a query, providing valuable insights into how your database is functioning. In this article, we'll take a deep dive into one of the most important columns: `type`.

### Const

At the top of the list, the `const` access method is one of the most efficient. `Const` access is only used when a primary key or unique index is in place, allowing MySQL to locate the necessary row with a single operation. When you see `const` in the type column, it's telling you that MySQL knows there is only one match for this query, making the operation as efficient as possible.

### Ref

The `ref` access method is slightly less efficient than `const`, but still an excellent choice if the right index is in place. `Ref` access is used when the query includes an indexed column that is being matched by an equality operator. If MySQL can locate the necessary rows based on the index, it can avoid scanning the entire table, speeding up the query considerably.

### Fulltext

MySQL provides an option to create full-text indexes on columns intended for text-based search queries. The `fulltext` access method is used when a full-text index is in place and the query includes a full-text search. `Fulltext` access allows MySQL to search the index and return the results quickly.

### Range

When you use `range` in the where clause, MySQL knows that it will need to look through a range of values to find the right data. MySQL will use the B-Tree index to traverse from the top of the tree down to the first value of the range. From there, MySQL consults the linked list at the bottom of the tree to find the rows with values in the desired range. It's essential to note that MySQL will examine every element in the range until a mismatch is found, so this can be slower than some of the other methods mentioned so far.

### Index

The `index` access method indicates that MySQL is scanning the entire index to locate the necessary data. `Index` access is the slowest access method listed so far, but it is still faster than scanning the entire table. When MySQL cannot use a primary or unique index, it will use `index` access if an index is available.

### All

Finally, the `all` access method means that MySQL is scanning the entire table to locate the necessary data. `All` is the slowest and least efficient access method, so it's one that you want to avoid as much as possible. MySQL may choose to scan the entire table when there is no suitable index, so this is an excellent opportunity to audit your indexing strategy.

### Improving query performance

Using explain types, you can gain insight into your query performance and identify areas for improvement. If you see `const` or `ref` access methods, you likely have a well-structured database that performs well. If you see `index` or `all` access methods, it might be time to investigate ways to optimize your database structure or indexing strategy.

By taking a proactive approach to query optimization, you can boost database performance and provide a better end-user experience. The `type` column is just one tool that you can use to gain insights into your data and improve query performance. Try experimenting with different types of queries and see how MySQL approaches them, using the `type` column to gauge the efficiency of your database's access methods.