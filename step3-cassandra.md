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
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 4</span>
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Load the CSV dataset into the table and execute queries</div>

✅ Load the data from the `videos_by_title_year.csv` file using the `COPY` command:
```
COPY videos_by_title_year (title, added_year, added_date, description, user_id, video_id) 
FROM 'assets/videos_by_title_year.csv' WITH HEADER=true;
```

✅ Try running queries on the `videos_by_title_year` table to query on a specific `title` and `added_year`:
```
SELECT * FROM videos_by_title_year WHERE title = 'Introduction To Apache Cassandra' AND added_year = 2014;
SELECT * FROM videos_by_title_year WHERE title = 'Sleepy Grumpy Cat' AND added_year = 2015;
SELECT * FROM videos_by_title_year WHERE title = 'Grumpy Cat: Slow Motion' AND added_year = 2015;
SELECT * FROM videos_by_title_year WHERE title = 'AzureDev' AND added_year = 2015;
```

✅ What error does Cassandra return when you try to query on just title or just year? Why?
```
SELECT * FROM videos_by_title_year WHERE title = 'Introduction To Apache Cassandra';
SELECT * FROM videos_by_title_year WHERE added_year = 2014;
```

These queries fail because of not using the whole partition key. Since both
`title` and `added_year` are part of the partition key, both are required to query.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
