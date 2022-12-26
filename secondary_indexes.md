These notes are based on different tables.
Take a look at the statements and don't struggle with switching tables and column names.
Focus on getting the idea.

Many performance issues can be traced back to queries that don't use secondary indexes.

This SQL shell command displays indexes from the customers table `SHOW INDEXES FROM customers;`

Find out which index is being used in a query like `EXPLAIN SELECT * FROM customers WHERE customer_id = 1;`

The logical query plan of the mentioned command looks like following:

```
 tree |    field    | description
+-----+-------------+-------------------+
      | distributed | false
      | vectorized  | false
 scan |             |
      | table       | customers@primary
      | spans       | /1-/1/#
 (5 rows)
 ```
 
The row `| table | customers@primary` indicates what index was used in the query.
 
Add a sencondary index `CREATE INDEX my_index ON users (last_name, first_name);`

Review the changes `SHOW INDEXES FROM users;`

See the advantage of this change `EXPLAIN SELECT * FROM users WHERE last_name = 'Cross' AND first_name = 'William';`

For more details on indexes https://www.cockroachlabs.com/docs/stable/indexes.html

For more details on SQL Tuning with EXPLAIN https://www.cockroachlabs.com/docs/stable/sql-tuning-with-explain.html
