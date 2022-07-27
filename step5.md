<div class="top">

# Updating rows
### [◂](command:katapod.loadPage?step4){.steps} Step 5 of 9 [▸](command:katapod.loadPage?step6){.steps}
</div>

We need to update information about the following user and his ratings:
```
SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

Update the user name and age:
```
UPDATE users SET name = 'Joseph', age = 26
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
```

Change the rating left by the user for one of the movies:
<details>
  <summary>Solution</summary>

```
UPDATE ratings_by_user SET rating = 3 
WHERE email = 'joe@datastax.com'
  AND title = 'Alice in Wonderland'
  AND year  = 2010;

SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

</details>

[continue](command:katapod.loadPage?step6){.orange_bar}