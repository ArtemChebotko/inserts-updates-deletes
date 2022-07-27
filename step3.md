<div class="top">

# Let's get started ...
### [◂](command:katapod.loadPage?step2){.steps} Step 3 of 9 [▸](command:katapod.loadPage?step4){.steps}
</div>

Start the CQL shell:
```
cqlsh
```

Create the keyspace:
```
CREATE KEYSPACE killr_video
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };
```

Set the current working keyspace:
```
USE killr_video;
```

Create the tables:
```
CREATE TABLE users (
  email TEXT,
  name TEXT,
  age INT,
  date_joined DATE,
  PRIMARY KEY ((email))
);
CREATE TABLE ratings_by_user (
  email TEXT,
  title TEXT,
  year INT,
  rating INT,
  PRIMARY KEY ((email), title, year)
);
```

[continue](command:katapod.loadPage?step4){.orange_bar}