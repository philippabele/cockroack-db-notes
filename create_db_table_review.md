Attach a terminal to one of the running nodes of the cluster.
This is possible because we launched the cluster with TLS disabled.

start the SQL Shell `cockroach sql --insecure`

create a database `create database crdb_uni;`

set database as current with `SET database = crdb_uni;`

add a table `CREATE TABLE students (id UUID PRIMARY KEY DEFAULT gen_random_uuid(), name STRING);`

review the created table `SHOW CREATE students;`

add a column `ALTER TABLE students ADD COLUMN schedule STRING;`

review the change `SHOW CREATE TABLE students;`
