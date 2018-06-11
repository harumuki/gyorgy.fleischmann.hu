---
layout:   post
title:    🖥 Batch rename
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [unix, development, how to]
---

A feladat az lenne, hogy át kell nevezni könyvtárakban lévő fájlokat. A fájlok nevében space is van: 

<!-- break -->

Erre az én megoldásom:

```shell
find . -type f -name "*copy.jpg" -exec sh -c 'mv "{}" "$( echo {} | sed 's/ copy/_ORIGINAL/' )"' \;
```

[Gist link](https://gist.github.com/FleXoft/61da9b1eadb6b5aab122a16bb279c564)