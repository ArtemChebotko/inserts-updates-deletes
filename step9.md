<div class="top">

# More capabilities
### [◂](command:katapod.loadPage?step8){.steps} Step 9 of 9 [▸](command:katapod.loadPage?step10){.steps}
</div>

CQL statements `INSERT`, `UPDATE` and `DELETE` offer several less commonly used and more advanced 
capabilities that you should be aware of, including:
- *Conditional inserts, updates and deletes*: a condition must be satisfied for an operation to succeed;
- *Inserts and updates with TTL*: inserted or updated data automatically expires after Time-to-Live (TTL) seconds;
- *Inserts, updates and deletes with timestamps*: mark inserted or updated values with write-time timestamps or 
  delete values whose write-time timestamps are older than the specified timestamp;
- *Inserts, updates and deletes for counters or collections*: operations that deal with the `COUNTER` data type or
  collection data types like `SET`, `LIST` and `MAP` use additional syntactic constructs.

We only demonstrate a couple of use cases for conditional statements here.

A conditional `INSERT` can be used to prevent an upsert when it matters, 
such as when two users try to register using the same email. Only the first 
`INSERT` should succeed:
```
INSERT INTO users (email, name, age, date_joined) 
VALUES ('art@datastax.com', 'Art', 33, '2020-05-04')
IF NOT EXISTS;
INSERT INTO users (email, name, age, date_joined) 
VALUES ('art@datastax.com', 'Arthur', 44, '2020-05-04')
IF NOT EXISTS;

SELECT * FROM users WHERE email = 'art@datastax.com';
```

A conditional `UPDATE` can also be used to prevent an upsert that may result from 
concurrent updates. For example, only the first `UPDATE` should succeed:
```
UPDATE users SET name = 'Artie'
WHERE email = 'art@datastax.com' IF name = 'Art';
UPDATE users SET name = 'Arthur'
WHERE email = 'art@datastax.com' IF name = 'Art';

SELECT * FROM users WHERE email = 'art@datastax.com';
``` 

[continue](command:katapod.loadPage?finish){.orange_bar}
