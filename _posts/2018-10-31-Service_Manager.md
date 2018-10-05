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

Menu Navigation: System Administration - Ongoing Maintenance > User Quick Add Utility

images/sm/poweruser1.png
images/sm/poweruser2.png

### Új menük készítése + hozzá parancsok

### Hogyan kell megtalálni egy menüt

### Hogyan kell létrezhoni

### $file

https://ernestodisanto.wordpress.com/2015/10/30/hpsm-current-file-variable-in-rad/

$file - Format Control
$File - Links
$L.file - minden más
$L.filed - Display App.

### Variables

$G. $lo Globális változók
$L. lokális változól

### Forms Designer

Hogyan készítsünk olyan Form-okat, amivel meg lehet könnyen találni a Globalists neveket vagy a Mezőneveket?

## Process Designer

Best Practices https://docs.microfocus.com/SM/9.52/Hybrid/Content/PD_tailoring_BPG/Process_Designer_Basic_Concepts.htm

Menu Navigation: Tailoring - Process Designer

### Fázisok ás átmenetek létrehozásának trükkjei

Menu Navigation: Tailoring - Process Designer - Workflows

1. - érdemes a fázisokat egyből létrehozni és azonnal elnevezni 
2. - figyelni kell, hogy a átmenet parancs nevének megadásánál felül fogja írni a mögötte lévé scmessage rekordot is!

sm/rule_naming.png 

### Alapértékek és kitöltések ellenőrzése [Rule Sets]

Menu Navigation: Tailoring - Process Designer - Rule Sets

sm/rule_set_default
sm/rule_set_via_javascript1
sm/rule_set_via_javascript2
sm/rule_set_mandatory_default

value="Unplanned Change Detection"
value="Rrrrisk ass"

A mezők nevénél nem magát a mezőnek a nevét kell megadni (amit a vastag kliensben a mezőt kijelölve és Ctrl-h nyomva tudunk megkapni, ha a Window - Preferences menüpontban a Service Manager almenüben az Appearance részében a "Show context-sensitive help debug information" opció be van kapcsolva)

sm/sm_client_windows_preferences1

, hanem a Data Policy-ben lévő Caption nevét kell megadni a mezőhivatkozásoknál.

### Lista ellenőrzése egy globális lista alapján

sm/rule_set_validate_against_list

A globálislista kiválasztásánal nem magát a globális lista változóját kell megadni, hanem a nevét. Ezt a legkönnyebben a Globális lista változójának kinyerése (vastag kliens, Forms Designer) után a  


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