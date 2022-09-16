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
 <a href='command:katapod.loadPage?[{"step":"step8-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 9 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"finish-astra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">More capabilities</div>

CQL statements `INSERT`, `UPDATE` and `DELETE` offer several less commonly used and more advanced 
capabilities that you should be aware of, including:
- *Conditional inserts, updates and deletes*: a condition must be satisfied for an operation to succeed;
- *Inserts and updates with TTL*: inserted or updated data automatically expires after Time-to-Live (TTL) seconds;
- *Inserts, updates and deletes with timestamps*: mark inserted or updated values with write-time timestamps or 
  delete values whose write-time timestamps are older than the specified timestamp;
- *Inserts, updates and deletes for counters or collections*: operations that deal with the `COUNTER` data type or
  collection data types like `SET`, `LIST` and `MAP` use additional syntactic constructs.

We only demonstrate a couple of use cases for conditional statements here.

✅ A conditional `INSERT` can be used to prevent an upsert when it matters, 
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

✅ A conditional `UPDATE` can also be used to prevent an upsert that may result from 
concurrent updates. For example, only the first `UPDATE` should succeed:
```
UPDATE users SET name = 'Artie'
WHERE email = 'art@datastax.com' IF name = 'Art';
UPDATE users SET name = 'Arthur'
WHERE email = 'art@datastax.com' IF name = 'Art';

SELECT * FROM users WHERE email = 'art@datastax.com';
``` 

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step8-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

