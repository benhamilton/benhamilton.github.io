---
layout: post
title: Jekyll Code Blocks
permalink: 2020-02-18-Jekyll-Code-Blocks
published: false
---
Testing of code blocks
<!--more-->

Using triple backticks:

```sql
select
    *
from
    tbl_contacts contacts
where
    contacts.isdeleted = '0';
```

and now using `pre` and `code` html tags:

<pre><code>select
    *
from
    tbl_contacts contacts
where
    contacts.isdeleted = '0';</code></pre>

Wrapped in a highlight tag


{% highlight sql %}
sql
select
    *
from
    tbl_contacts contacts
where
    contacts.isdeleted = '0';
{% endhighlight %}

