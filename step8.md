<div class="top">

# Updating primary key columns
### [◂](command:katapod.loadPage?step7){.steps} Step 8 of 9 [▸](command:katapod.loadPage?step9){.steps}
</div>

One of our users wants to change his email from *joe@datastax.com* to
*joseph@datastax.com*. There are three rows in two tables that we need to update:
```
SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

We know that primary key column values cannot change, but we can try anyway.
Update the user email:
```
-- This will result in an error
UPDATE users SET email = 'joseph@datastax.com'
WHERE email = 'joe@datastax.com';
```

The right solution is to insert a new row and delete the old one:
```
INSERT INTO users (email, name, age, date_joined) 
VALUES ('joseph@datastax.com', 'Joe', 25, '2020-01-01');
DELETE FROM users
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM users WHERE email = 'joseph@datastax.com';
```

Change the remaining two rows:
<details>
  <summary>Solution</summary>

```
INSERT INTO ratings_by_user (email, title, year, rating) 
VALUES ('joseph@datastax.com', 'Alice in Wonderland', 2010, 9);
INSERT INTO ratings_by_user (email, title, year, rating)  
VALUES ('joseph@datastax.com', 'Edward Scissorhands', 1990, 10);
DELETE FROM ratings_by_user
WHERE email = 'joe@datastax.com';

SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
SELECT * FROM ratings_by_user WHERE email = 'joseph@datastax.com';
```

</details>

[continue](command:katapod.loadPage?step9){.orange_bar}
