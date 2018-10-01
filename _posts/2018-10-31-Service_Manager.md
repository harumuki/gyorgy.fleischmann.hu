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

Menu Navigation: Tailoring - Process Designer

### Fázisok ás átmenetek létrehozásának trükkjei

Menu Navigation: Tailoring - Process Designer - Workflows

1. - érdemes a fázisokat egyből létrehozni és azonnal elnevezni 
2. - figyelni kell, hogy a átmenet parancs nevének megadásánál felül fogja írni a mögötte lévé scmessage rekordot is!

sm/rule_naming 

### Alapértékek és kitöltések ellenőrzése [Rule Sets]

Menu Navigation: Tailoring - Process Designer - Rule Sets

sm/rule_set_via_javascript1
sm/rule_set_via_javascript2
sm/rule_set_via_javascript3
sm/rule_set_mandatory_default

value="Unplanned Change Detection"
value="Rrrrisk ass"

A mezők nevénél nem magát a mezőnek a nevét kell megadni (amit a vastag kliensben a mezőt kijelölve és Ctrl-h nyomva tudunk megkapni, ha a Window - Preferences menüpontban a Service Manager almenüben az Appearance részében a "Show context-sensitive help debug information" opció be van kapcsolva), hanem a Data Policy-ben lévő

### Lista ellenőrzése egy globális lista alapján

sm/rule_set_validate_against_list

A globálista kiválasztásánal nem magát a globális lista változóját kell megadni, hanem a nevét. Ezt a legkönnyebben 

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