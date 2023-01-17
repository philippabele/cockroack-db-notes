# locality

SQL command to see the region localities of the table movr.users

`SHOW RANGES FROM TABLE movr.users;`

See demo at https://www.youtube.com/watch?v=pTCeMw5WnJk

# multi-region

keywords

CockroachDB multi-region capabilities make it easier to run global applications. To use these capabilities effectively, you should understand the following concepts:

    - Cluster region is a geographic region that you specify at node start time.
    - Database region is a geographic region in which a database operates. You must choose a database region from the list of available cluster regions.
    - Survival goal dictates how many simultaneous failure(s) a database can survive.
    - Table locality determines how CockroachDB optimizes access to a table's data.


https://www.cockroachlabs.com/docs/stable/multiregion-overview.html

https://www.youtube.com/watch?v=C5MEI6Cve30