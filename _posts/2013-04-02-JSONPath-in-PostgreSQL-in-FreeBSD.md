---
layout: post
title: JSONPath in PostgreSQL in FreeBSD
meta: via pg-jsonpath & plv8js
---

# {{ page.title }}

Sadly, in postgresql 9.2.3 you have json type built-in but no functions to work with it.
JSONPath is absolutely needed. In past we used some custom code, now I wanted something stable & supported.
Japanese guy choplin [did the great job](http://www.chopl.in/blog/2012/12/21/introduction-of-pg-jsonpath/). Seriously, I think that simpler is better. [Github page](https://github.com/choplin/pg-jsonpath) probably will be easier for you to read.
It's wrapper for JSONPath implemented in javascript. To run javascript code in postgres you need [plv8](http://code.google.com/p/plv8js/wiki/PLV8).
plv8 [will hang on freebsd](http://lists.freebsd.org/pipermail/freebsd-ports-bugs/2013-February/248825.html) if postgres is build without PTHREAD support.
So, rebuild postgresql from ports with ${PTHREAD_LIBS} enabled (from previous link).
Get plv8js and apply [patch](http://code.google.com/p/plv8js/issues/detail?id=59) to it.
Install plv8js and pg-jsonpath and you are done.