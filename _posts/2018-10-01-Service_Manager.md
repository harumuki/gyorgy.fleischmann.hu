---
layout:   post
title:    MicroFocus / HPE / HP Service Manager  
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [microFocus, hpe, hp, service manager, sm, how to]
---

Akkor fussunk is neki az alapoknak!

## A tesztkörnyezet

A tesztrendszer SM verziója: **v9.60**, operációs rendszerei:
<pre class="terminal">
Linux hpsm 3.10.0-862.11.6.el7.x86_64 #1 SMP Tue Aug 14 21:49:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
</pre>
<pre class="terminal">
Linux oracle01.eg.office 4.1.12-124.18.6.el7uek.x86_64 #2 SMP Wed Aug 15 19:12:26 PDT 2018 x86_64 x86_64 x86_64 GNU/Linux
</pre>

A tesztrendszer WEB felületét itt lehet lérni: [http://mysmdev:8080/sm/index.do?lang=en](http://mysmdev:8080/sm/index.do?lang=en) (ez a cím persze csak nálunk házon belül működik!)

[login kép]

# Service Manager

## Alap dolgok

### Session TimeOut

Menu Navigation: System Administration - Ongoing Maintenance - System - Start Inactivity Timer

### Ikonok

A munkafolyamatokhoz felhasználható ikonok a /opt/tomcat/webapps/sm/images/obj16 könyvtárban találhatóak.

tnext_ph.png

tprior_p.png

### Új power user létrehozása

### Új menük készítése + hozzá parancsok

### Hogyan kell megtalálni egy menüt

### Hogyan kelllétrezhoni


## Process Designer

### Fázisok ás átmenetek létrehozásának trükkjei

### Alapérték kitöltések ellenőrzése

### Lista ellenőrzése

### Mentés előtti mező kitöltöttség ellenőrzése

### Dátum összehasonlítása és ellenőrzése

### Időzített fázisátmenetek és ellenőrzésük 

### Globális szabályok egy munkafolyamatra

### Más tábla alapján történő ellenőrzés

### Operátor rekord email címe alapján ellenőrzés, javascript, debug

email in $L.file~=null

DEBUG javascript:
```javascript
var f = new SCFile( "operator", SCFILE_READONLY );
var query = "name=\"" + vars['$L.file']['coordinator'] + "\"";
var rc = f.doSelect( query );

if ( rc==RC_SUCCESS ) {
    print( f.email );
}
else { 
    print( "Email Not found!" ); 
}
```

### Jóváhagyások

### Új változáskezelési kategória felvétele

Menu Navigation: Change management - Configuration - Change Categories