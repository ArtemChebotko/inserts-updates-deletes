<div class="top">

# Inserts, updates, deletes and upserts
### [◂](command:katapod.loadPage?intro){.steps} Step 1 of 9 [▸](command:katapod.loadPage?step2){.steps}
</div>

Data manipulation operations in Apache Cassandra™ include *inserts*, *updates* and *deletes*, and have respective CQL statements 
`INSERT`, `UPDATE` and `DELETE`. They are used to add, change, and remove rows and column values in Cassandra tables.
While their general semantics is easy to understand and their syntax is similar to the respective operations in relational databases
and SQL, there are also important differences.

All three operations are *write* operations. Inserts write new data into tables. Similarly, updates write new data into tables.
Even deletes write markers, called *tombstones*, to signify that data is now removed. Since there is *no read before a write*, 
the operations do their writes regardless of whether a row with the same primary key already exists in a table or not. Consider the following 
three situations. First, when inserting a new row into a table and the table already has a row with the same primary key, 
the existing row will effectively be updated. In other words, the insert operation will *upsert* data into the existing row. 
Second, when updating a row that does not exist in a table, the row will be inserted into the table. In other words, 
the update operation will *upsert* the new row into the table. You can think about an *upsert* as an insert that causes an update or 
an update that causes an insert. Finally, when deleting a row that does not exist in a table, a tombstone 
will simply be written.

It is also worth mentioning, that Cassandra does support more expensive *conditional* inserts, updates and deletes 
that implement the read-before-write pattern. We will see examples of those, too.


[continue](command:katapod.loadPage?step2){.orange_bar}