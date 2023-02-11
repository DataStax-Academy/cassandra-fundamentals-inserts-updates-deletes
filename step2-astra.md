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
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 9</span>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Syntax</div>

For inserting updating and deleting rows and columns in Cassandra tables, Cassandra Query Language 
provides statements `INSERT`, `UPDATE` and `DELETE` with the following simplified syntax:

<pre class="non-executable-code">
INSERT INTO [keyspace_name.] table_name 
       (column_name  [ , ... ]) 
VALUES (column_value [ , ... ]);

UPDATE [keyspace_name.] table_name
SET column_name = column_value [ , ... ] 
WHERE primary_key_column_name = value [ AND ... ];

DELETE [column_name][ , ... ]
FROM [keyspace_name.] table_name 
WHERE primary_key_column_name = value [ AND ... ];
</pre>

All statements require *keyspace name* and *table name* to identify an existing table to 
perform an operation on. If a *keyspace name* is omitted, the current working keyspace is used.

The `INSERT` statement inserts a new row into a table or upserts data into an existing row. 
All primary key columns and their values must be 
specified to identify a row.

The `UPDATE` statement updates individual non-key columns in an existing row or upserts a new row. All 
primary key columns and their values must be 
specified in the `WHERE` clause to identify a row.

The `DELETE` statement removes an entire partition, a subset of rows in a partition or an individual row; 
when column names are specified, only selected non-key columns are removed. 
The `WHERE` clause uses primary key columns to identify one or more rows in a partition.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
