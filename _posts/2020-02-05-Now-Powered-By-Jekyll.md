---
layout: post
title: Now Powered By Jekyll
permalink: 2020-02-05-now-powered-by-jekyll
published: true
---
I've now cut-over from [WordPress](https://wordpress.org/) to [Jekyll](https://jekyllrb.com/) to run this site.<!--more-->

I have over the last couple of years played with Jekyll, but haven't committed to it until now. On the 13th of January 2020, I bit the bullet and setup [Jekyll Now](https://ben.hamilton.id.au/Hello-Jekyll-Now/) and since then until today have slowly chipped away at doing the migration.

Today the DNS records cut-over and it's now live.

The basic setup is that I create/edit posts in a git repo, when I commit the additions/edits, that triggers an action that transforms the source markdown files into static html and css to display this site.

I've done this for a few reasons that I'll list here:

1. It's now a static site, meaning I've got a lot more portability (I can move the site between hosts much easier, no databases to fiddle with).
2. When hosted on the same equipment, it's faster. It's just serving up static files, no database queries, no building the pages on the fly.
3. I can understand how it builds every part of the site (it's been a great learning experience for me).
4. I can edit online or offline, just one commit away from being live.
5. I can run the entire site locally - from my desktop, laptop or even from a [Raspberry Pi](https://dave.thwaites.org.uk/website/installing-jekyll.html).

So now it's up and live, I'm happy :)
