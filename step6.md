<div class="top">

# Deleting rows
### [◂](command:katapod.loadPage?step5){.steps} Step 6 of 9 [▸](command:katapod.loadPage?step7){.steps}
</div>

Let's delete all data from our tables.

Delete one column in a row:
```
DELETE age FROM users
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
```

Delete a row:
```
DELETE FROM ratings_by_user
WHERE email = 'joe@datastax.com'
  AND title = 'Alice in Wonderland'
  AND year  = 2010;
  
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

Delete all rows in a partition:
```
DELETE FROM ratings_by_user
WHERE email = 'joe@datastax.com';
  
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

Delete the remaining rows in the tables:
<details>
  <summary>Solution</summary>

```
SELECT * FROM users;
SELECT * FROM ratings_by_user;

DELETE FROM users
WHERE email = 'joe@datastax.com';
DELETE FROM users
WHERE email = 'jen@datastax.com';
DELETE FROM ratings_by_user
WHERE email = 'jen@datastax.com';

SELECT * FROM users;
SELECT * FROM ratings_by_user;
```

</details>

[continue](command:katapod.loadPage?step7){.orange_bar}