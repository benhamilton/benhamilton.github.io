---
layout: post
title: How to Convert a Number From Negative to Positive
permalink: 2020-02-20-convert-number-negative-to-positive
published: true
---
Doing a calculation today to see how many hours a support case is open, using the following sugarlogic formula:

```javascript
hoursUntil($date_entered)
```
I get a negative value returned. Whilst accurate, the client is wanting to see this as a positive integer, not a negative integer.

So the question I had was "How do I convert a negative number to a positive number?"<!--more-->

It's quite simple really, you wrap it in the `abs()` function. This will return the *absolute value* of a number.

Thus the resulting sugarlogic formula is:

```javascript
abs(hoursUntil($date_entered))
```
