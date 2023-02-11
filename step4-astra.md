<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Inserts, Updates, Deletes and Upserts in Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Inserting rows</div>

We are ready to populate tables `users` and `ratings_by_user` with the following rows:

| email            | name | age | date_joined |
|------------------|------|-----|-------------|
| <span style="background-color:#F5B7B1">joe@datastax.com</span> |  Joe |  25 |  2020-01-01 |
| <span style="background-color:#AED6F1">jen@datastax.com</span> |  Jen |  27 |  2020-01-01 | 

| email            | title               | year | rating |
|------------------|---------------------|------|--------|
| <span style="background-color:#F5B7B1">joe@datastax.com</span> | Alice in Wonderland | 2010 |      9 |
| <span style="background-color:#F5B7B1">joe@datastax.com</span> | Edward Scissorhands | 1990 |     10 |
| <span style="background-color:#AED6F1">jen@datastax.com</span> | Alice in Wonderland | 1951 |      8 |
| <span style="background-color:#AED6F1">jen@datastax.com</span> | Alice in Wonderland | 2010 |     10 |

<br/>

✅ Insert the row into table `users`:
```
INSERT INTO users (email, name, age, date_joined) 
VALUES ('joe@datastax.com', 'Joe', 25, '2020-01-01');
```

✅ Insert the rows into table `ratings_by_user`:
```
INSERT INTO ratings_by_user (email, title, year, rating) 
VALUES ('joe@datastax.com', 'Alice in Wonderland', 2010, 9);
INSERT INTO ratings_by_user (email, title, year, rating)  
VALUES ('joe@datastax.com', 'Edward Scissorhands', 1990, 10);
```

✅ Retrieve all rows from the tables:
```
SELECT * FROM users;
SELECT * FROM ratings_by_user;
```

<br/>
<br/>

We only inserted a half of the rows shown above and left 
the other half for you to practice!

✅ Insert the remaining rows into the tables:
<details>
  <summary>Solution</summary>

```
INSERT INTO users (email, name, age, date_joined) 
VALUES ('jen@datastax.com', 'Jen', 27, '2020-01-01');

INSERT INTO ratings_by_user (email, title, year, rating)  
VALUES ('jen@datastax.com', 'Alice in Wonderland', 1951, 8);
INSERT INTO ratings_by_user (email, title, year, rating) 
VALUES ('jen@datastax.com', 'Alice in Wonderland', 2010, 10);

SELECT * FROM users;
SELECT * FROM ratings_by_user;
```

</details>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

