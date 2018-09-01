---
layout:   post
title:    Google Analytics kód frissítése
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [unix, development, how to]
---

A mostani feladat az lenne, hogy le kellene cserélni a régi Google Analitics kódot az összes régi .htm oldalon az újra és persze akkor a régi karakterkódolást iso-8859-2 is GitHub Pages kompatibilissé (UTF-8) kellene tenni:

<!-- break -->

Legyen itt két link segítségnek:

- Itt Regexp kifejezéseket lehet nagyon kényelmes módon tesztelni: https://regexr.com/
- Itt pedig a perl parancs paraméterei találhatóak [http://perldoc.perl.org/perlrun.html#*-0*\[_octal/hexadecimal_\]](http://perldoc.perl.org/perlrun.html#*-0*[_octal/hexadecimal_])

És akkor a megoldás két külön parancsban:

```shell
find . -name '*htm' -print -exec \
  perl -0777 -pi -e 's/<script src="http:\/\/www.google-analytics.com\/urchin.js" type="text\/javascript">\n<\/script>\n<script type="text\/javascript">\n_uacct = "UA-1485101-1";\nurchinTracker\(\);\n<\/script>/<!-- Global site tag \(gtag.js\) - Google Analytics -->\n<script async src="https:\/\/www.googletagmanager.com\/gtag\/js?id=UA-108075264-2"><\/script>\n<script>\nwindow.dataLayer = window.dataLayer || \[\];\nfunction gtag\(\){dataLayer.push\(arguments\);}\ngtag\('js', new Date()\);\n\ngtag\('config', 'UA-108075264-2'\);\n<\/script>\n/gm' {} \
\;
```

```shell
find . -name '*htm' -print -exec \
 recode iso-8859-2..utf8 {} \
\;
```