<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Inserts, Updates, Deletes and Upserts in Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step7-cassandra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 8 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"step9-cassandra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Updating primary key columns</div>

✅ One of our users wants to change his email from *joe@datastax.com* to
*joseph@datastax.com*. There are three rows in two tables that we need to update:
```
SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

✅ We know that primary key column values cannot change, but we can try anyway.
Update the user email:
```
-- This will result in an error
UPDATE users SET email = 'joseph@datastax.com'
WHERE email = 'joe@datastax.com';
```

✅ The right solution is to insert a new row and delete the old one:
```
INSERT INTO users (email, name, age, date_joined) 
VALUES ('joseph@datastax.com', 'Joe', 25, '2020-01-01');
DELETE FROM users
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM users WHERE email = 'joseph@datastax.com';
```

✅ Change the remaining two rows:
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

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step7-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step9-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

