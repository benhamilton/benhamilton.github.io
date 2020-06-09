---
layout: post
Title: Jekyll Now Reinstall
permalink: 2020-06-09-jekyll-now-reinstall
published: true
---
Having migrated to a new laptop, I needed to reinstall Jekyll Now. And it failed. But then it worked.<!--more-->

Because I was able to clone the git repo to my local, and that repo was already configured/set for publishing to github pages, all I needed to do was install github pages locally, rather than Jekyll etc.

I could make changes, commit the change, push it and it would appear on the live site, but I couldn't preview it locally with Jekyll. Hence why github pages locally installed, it contains Jekyll.

However, when trying to install `github-pages` I was getting this error:

```zsh
	gem install github-pages
	ERROR:  While executing gem ... (Gem::FilePermissionError)
		You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.
```

Using the instuctions kindly noted by [Antonio Cangiano](https://programmingzen.com/installing-rbenv-on-zsh-on-macos/) at Programming Zen<sup id="fnbl-20200609171844"><a href="#fn-20200609171844">1</a></sup>.

Summary below (Antonio explains it in more detail)

```zsh
	brew update && brew install rbenv ruby-build
	export path="$HOME/.rbenv/bin:$PATH"
```

Add the following to `.zshenv`

```zsh
	export PATH="$HOME/.rbenv/bin:$PATH"
```

Added the following to `.zshrc`

```zsh
	source $HOME/.zshenv
	eval "$(rbenv init - zsh)"
```

Restart the iterm2 and run the following commands

```zsh
	rbenv install 2.6.5
	rbenv global 2.6.5
```

Restart iterm2 and run the following command

```zsh
	ruby -v
```

You should see something like: `ruby 2.6.5p114 (2019-10-01 revision 67812) [x86_64-darwin19]` returned

Then run this command

```zsh
	ruby -e "puts (1..100).reduce(:+)"
```

You should see `5050` returned

Now install github-pages

```zsh
	gem install github-pages
```

Now when running `jekyll serve` in the root of the local repo, I can use a browser to view the site before issuing a `git push`.

---

<ol>
	<li id="fn-20200609171844">
		<p>He was getting a similar error for htmlbeautifier. His explaination contains more detail.<a href="#fnbl-20200609171844" class="FootNoteBackLink" title="Jump back to footnote 1 in the text.">↩︎</a></p>
	</li>
</ol>
