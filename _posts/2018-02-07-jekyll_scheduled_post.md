---
layout:   post
title:    ⏰ Időzített Jekyll bejegyzés
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [jekyll, web, how to]
---

A legegyszerűbb, leghasználhatóbb választ ez a poszt adja + erre a problémára: [http://code.alxmjo.com/how-to-schedule-posts-with-jekyll/](http://code.alxmjo.com/how-to-schedule-posts-with-jekyll/)

<!-- break -->

Az én Jekyll konfigurációs fájlomban: [_config.yml](https://github.com/FleXoft/gyorgy.fleischmann.hu/blob/master/_config.yml) beállított:

```
future: false
```

opción kívül a megoldáshoz kell majd még egy olyan gép, ami időről időre meg tudja hívni én konkrét Jekyll oldalamhoz / repository-mhoz ezt a parancsot:

<pre class="terminal">curl "https://api.github.com/repos/FleXoft/gyorgy.fleischmann.hu/pages/builds" \
-X POST \
-H 'Authorization: token 7a65376e4b10e090037b4c82338c4ef5031ab408' \
-H "Accept: application/vnd.github.mister-fantastic-preview"</pre>

Az API token-t a [Settings → Personal access tokens](https://github.com/settings/tokens/) linken lehet generálni a GitHub-on, fentebb csak egy példa szerepel.

/* Ez a bejegyzés is már ezzel élesedett. */