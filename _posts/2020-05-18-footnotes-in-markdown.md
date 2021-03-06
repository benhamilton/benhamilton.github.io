---
layout: post
title: Footnotes in Markdown
permalink: 2020-05-18-footnotes-in-markdown
published: true
---

Using markdown is great. Creating and using footnotes in markdown is very manual. Painful even.

So I've created a Keyboard Maestro shortcut to make them easier.<!--more-->

![Keyboard Maestro Markdown Footnote Marcro](../images/kbm-mdfn.png)

What it does is run a shell script to get the current date and time and saves that to a variable.

Then we *insert by typing* the HTML code to do the superscript<sup id="fnbl-20200519095757"><a href="#fn-20200519095757">1</a></sup> for the foot note.

We use the date-time variable to create a footnote id to go at the bottom of the document (ie `fn-yyyymmddhhmmss`) and a slight variation for the backlink back up to where the footnote was inserted (i.e. `fnbl-yyyymmddhhmmss`).

Then a line below insert an ordered list with a list item where the footnote text goes. Of course, we then move that to the bottom of the document. 

If we have more than one, manually update the number used for the footnote. Because the list of footnotes at the end are in an ordered list, they will be numbered automatically.

If you've got a way to further automate this please let me know.

[Download the macro](../images/kbm-mdfn.kmmacros)

<ol>
	<li id="fn-20200519095757">
		<p>Text of footnote goes here. <a href="#fnbl-20200519095757" class="FootNoteBackLink" title="Jump back to footnote 1 in the text.">↩︎</a></p>
	</li>
</ol>

