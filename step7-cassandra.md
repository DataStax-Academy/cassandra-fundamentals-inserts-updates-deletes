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
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"step8-cassandra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Upserting rows</div>

Since our tables `users` and `ratings_by_user` are now empty, we need to populate them again 
with the same data. This time, however, let's only use statements `INSERT` and `UPDATE` to always perform *upserts*.

✅ If you are not sure that your tables are empty, truncate them:
```
TRUNCATE TABLE users;
TRUNCATE TABLE ratings_by_user;
```

✅ Upsert the new rows:
```
UPDATE users 
SET name = 'Joe', date_joined = '2020-01-01'
WHERE email = 'joe@datastax.com';
UPDATE users 
SET name = 'Jen', date_joined = '2020-01-01'
WHERE email = 'jen@datastax.com';

UPDATE ratings_by_user 
SET rating = -9
WHERE email = 'joe@datastax.com'
  AND title = 'Alice in Wonderland'
  AND year  = 2010;
UPDATE ratings_by_user 
SET rating = -10
WHERE email = 'joe@datastax.com'
  AND title = 'Edward Scissorhands'
  AND year  = 1990;
UPDATE ratings_by_user 
SET rating = -8
WHERE email = 'jen@datastax.com'
  AND title = 'Alice in Wonderland'
  AND year  = 1951;
UPDATE ratings_by_user 
SET rating = -10
WHERE email = 'jen@datastax.com'
  AND title = 'Alice in Wonderland'
  AND year  = 2010;
  
SELECT * FROM users;
SELECT * FROM ratings_by_user;  
```

✅ Upsert the incomplete or incorrect column values:
```
INSERT INTO users (email, age) 
VALUES ('joe@datastax.com', 25);
INSERT INTO users (email, age) 
VALUES ('jen@datastax.com', 27);

INSERT INTO ratings_by_user (email, title, year, rating) 
VALUES ('joe@datastax.com', 'Alice in Wonderland', 2010, 9);
INSERT INTO ratings_by_user (email, title, year, rating)  
VALUES ('joe@datastax.com', 'Edward Scissorhands', 1990, 10);
INSERT INTO ratings_by_user (email, title, year, rating)  
VALUES ('jen@datastax.com', 'Alice in Wonderland', 1951, 8);
INSERT INTO ratings_by_user (email, title, year, rating) 
VALUES ('jen@datastax.com', 'Alice in Wonderland', 2010, 10);

SELECT * FROM users;
SELECT * FROM ratings_by_user;
```

Notice how we inserted new rows using `UPDATE` and updated existing rows using `INSERT`. 
This is what upserts are all about. `UPdate` and `inSERT` are really similar write operations 
under the hood, even though their syntax looks different on the surface.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step8-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

