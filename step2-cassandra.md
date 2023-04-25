<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Exercise 2.1: Working with Partitions</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:academy@datastax.com">email</a>.</span>
  </div>
</div>


<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step1-cassandra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 4</span>
 <a href='command:katapod.loadPage?[{"step":"step3-cassandra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create a keyspace and table in the CQL shell:</div>

✅ Start the CQL shell:
```
cqlsh
```

✅ Create a keyspace called `killrvideo` and switch to that keyspace. Use `NetworkTopologyStrategy` for the replication class and set the replication factor of `1` for datacenter `DC-Houston`. Remember the `USE` command switches keyspaces.
```
CREATE KEYSPACE IF NOT EXISTS killrvideo
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };

USE killrvideo;
```

✅ Create a table called `videos_by_title_year` with the same structure as shown in the previous step. Be sure users can query this table on both `title` and `added_year` by combining them into the partition key.
```
CREATE TABLE videos_by_title_year ( 
  title TEXT,
  added_year INT,
  added_date TIMESTAMP,
  description TEXT,
  user_id UUID,
  video_id TIMEUUID,
  PRIMARY KEY ((title, added_year))
);
```


<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
