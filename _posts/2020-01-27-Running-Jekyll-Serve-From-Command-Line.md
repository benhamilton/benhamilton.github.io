---
layout: post
title: Running Jekyll Serve From Command Line
permalink: 2020-01-27-Running-Jekyll-Serve-From-Command-Line
published: true
---

When working with a Jekyll site locally, it's useful to use the command `jekyll serve` to be able to view the site locally. However this ties up a terminal window. How to not keep a terminal window busy?<!--more-->

There are two methods.

First up, we can simply add an ampersand to the end of the command:
<pre><code>jekyll serve &
</code></pre>

Which gives us output similar to the below:
<pre><code>$ jekyll serve &
[1] 76710
ben@desktop ~/git/benhamilton.github.io master  Configuration file: /Users/ben/git/benhamilton.github.io/_config.yml
            Source: /Users/ben/git/benhamilton.github.io
       Destination: /Users/ben/git/benhamilton.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 5.473 seconds.
 Auto-regeneration: enabled for '/Users/ben/git/benhamilton.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
</code></pre>

What this does is tell the process to go to the background. We can then do other things in this terminal window.

So how do we stop the process when we want?

When it ran, see output above, the first lines it gave us said `[1] 76710` That number, *76710* (it'll be different on your machine) is the process ID.

Entering `kill 76710` (*replace the process ID with your process ID*) will kill the process.

What if we've forgotten what the process number is?

The command
<pre><code>ps -ax | grep jekyll
</code></pre>

will give the process number to us.

Sounds good. But wait, there is a catch.

If we close the terminal window, we stop that process. If we want the process to keep running *even* if we close the terminal window, this next command is for you.

Our second method is:

<pre><code>nohup jekyll serve
</code></pre>

The `nohup` command will run the command you give it in the background.
