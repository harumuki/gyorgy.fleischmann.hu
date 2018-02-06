---
layout:   post
title:    ⏰ Időzített Jekyll bejegyzés
author:   flex
comments: true
category: development / fejlesztés
tags:     [jekyll, web, development]
---

A legegyszerűbb, leghasználhatóbb választ ez a poszt adja + erre a problémára: [http://code.alxmjo.com/how-to-schedule-posts-with-jekyll/](http://code.alxmjo.com/how-to-schedule-posts-with-jekyll/)

A megoldáshoz kell majd egy olyan gép, ami időről, időre meg tudja hívni én konkrét Jekyll oldalamhoz ezt a parancsot:

<pre class="terminal">curl "https://api.github.com/repos/FleXoft/gyorgy.fleischmann.hu/pages/builds" \
-X POST \
-H 'Authorization: token 7a65376e4b10e090037b4c82338c4ef5031ab408' \
-H "Accept: application/vnd.github.mister-fantastic-preview"</pre>

/* Ez a bejegyzés is már ezzel élesedett. */