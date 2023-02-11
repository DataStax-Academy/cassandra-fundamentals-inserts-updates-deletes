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
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 5 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Updating rows</div>

✅ We need to update information about the following user and his ratings:
```
SELECT * FROM users WHERE email = 'joe@datastax.com';
SELECT * FROM ratings_by_user WHERE email = 'joe@datastax.com';
```

✅ Update the user name and age:
```
UPDATE users SET name = 'Joseph', age = 26
WHERE email = 'joe@datastax.com';

SELECT * FROM users WHERE email = 'joe@datastax.com';
```

✅ Change the rating left by the user for one of the movies:
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

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

