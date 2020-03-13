---
layout:   post
title:    mediaklikk.hu letöltés
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [unix, development, how to]
---

A feladat az lenne most, hogy töltsünk le egy korábbi műsort a [https://mediaklikk.hu/](https://mediaklikk.hu/)-ról.

Keressük meg és válasszuk ki a műsort, majd a felugró lejátszós ablakban nyomjunk egy jobbgomb "Inspect" menüt:

<center><img class="shadow" src="images/kossuth/screenshot_1.png" style="width: 60%;"></center>

Majd a consol-ba írjuk be a varázspanacsot, ami megadja a műsor tényleges .mp3 fájljának az elérési útját. 

<pre>console.log(urlFinal);</pre>

<center><img class="" src="images/kossuth/screenshot_2.png" style="width: 60%;"></center>

A megkapott linket másoljuk ki és a kedvenc módszerünkkel töltsük le és vágjuk szét, ha kell:

<pre class="terminal">
wget https://hangtar-cdn.connectmedia.hu/20200307090500/20200307094000/mr1.mp3
ffmpeg -ss "08:47.400" -to "15:40" -i "mr1.mp3" "Hajdu Balázs 2016 - Kidolgozott férfi test kontra vicces elme.mp3"
</pre>