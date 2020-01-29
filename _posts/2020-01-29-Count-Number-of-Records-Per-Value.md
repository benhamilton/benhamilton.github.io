---
layout: post
title: Count Number of Records Per Value
permalink: 2020-01-29-Count-Number-of-Records-Per-Value
published: true
---
Working with a SQL database today, wanted to know how different values there were in a column, and how many records each of those values had. The sql snippet here give me that answer. <!--more-->

<pre><code>SELECT
  client_rep as Representative,
  COUNT(*) AS NumberOfRecords
FROM
  contacts
GROUP BY
  client_rep
</code></pre>

What this turned up was there there were some records that had blank values, which, as it turns out, was VERY helpful to know.
