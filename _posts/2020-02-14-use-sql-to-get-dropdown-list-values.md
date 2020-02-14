---
layout: post
title: Use SQL to Get Dropdown List Values
permalink: 2020-02-14-use-sql-to-get-dropdown-list-values
published: true
---

We've got an application (Act!) that uses MSSQL as it's backend. There is a dropdown list in there, and we want get a list of all the dropdown values that are in use, and also how many records use each value.

Thus this, SQL snippet does that.<!--more-->

<pre><code>SELECT
  DROPDOWN_FIELDNAME,
  COUNT(*) AS 'NumberOfRecords'
FROM
  TBL_TABLENAME
GROUP BY
  DROPDOWN_FIELDNAME
ORDER BY 'NumberOfRecords' DESC;</code></pre>

Replace the DROPDOWN_FIELDNAME in both places, and replace the TBL_TABLENAME with your table name.

That gave me a result like follows:

| DROPDOWN_FIELDNAME | NumberOfRecords |
|:-------------------|----------------:|
| Alice | 903 |
| Bob | 431 |
| Carol | 206 |
| Dorothy | 140 |
| Evan | 58 |
| Frank | 42 |
| Gwen | 34 |
| Harold | 29 |
| Ian |  4 |
| Jane | 1 |

Hope you find that as useful as we have.
