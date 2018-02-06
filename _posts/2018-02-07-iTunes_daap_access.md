---
layout:   post
title:    📢 Otthoni megosztott Apple iTunes elérése VPN-en keresztül
author:   flex
comments: true
category: development / fejlesztés 
tags:     [iTunes, vpn, development, OS X, macOS, DAAP]
---

A feladat az, hogy elérehető legyen az otthoni (iTunes, DAAP, Digital Audio Access Protocol) zenearzenál is VPN-en keresztül. 

Sok más megoldás ([link1](http://theriom.com/Access-your-Bonjour-printer-over-VPN-from-your-iOS-device)) közül nekem végül ez a cikk tetszett meg a legjobban az 1szerűsége miatt: [Using iTunes Library Sharing over a VPN or the Internet](https://www.joshcurry.co.uk/posts/using-itunes-library-sharing-over-a-vpn-or-the-internet).

Lefuttatva még otthon ezt a parancsot: 

<pre class="terminal">dns-sd -Z _daap._tcp</pre>

megkapjuk az [elérhető szolgáltatások](https://developer.apple.com/library/content/qa/qa1312/_index.html) listáját. Jelen esetben csak a Digital Audio Access Protocol szolgáltatásokat szeretnénk összeszedni és én ezt a listát kaptam:

```
Browsing for _daap._tcp
DATE: ---Tue 06 Feb 2018---
 6:58:23.812  ...STARTING...

; To direct clients to browse a different domain, substitute that domain in place of '@'
lb._dns-sd._udp                                 PTR     @

; In the list of services below, the SRV records will typically reference dot-local Multicast DNS names.
; When transferring this zone file data to your unicast DNS server, you'll need to replace those dot-local
; names with the correct fully-qualified (unicast) domain name of the target host offering the service.

_daap._tcp                                      PTR     MUZAX._daap._tcp
MUZAX._daap._tcp                                SRV     0 0 3689 BLACKHOLE.local. ; Replace with unicast FQDN of target host
MUZAX._daap._tcp                                TXT     "txtvers=1" "Database ID=" "Machine ID=" "Machine Name=MUZAX" "mtd-version=0.2.4.1" "iTSh Version=131073" "Version=196610" "Password=false"

_daap._tcp                                      PTR     flex’s\032MacBook\032Pro\032Library_PW._daap._tcp
flex’s\032MacBook\032Pro\032Library_PW._daap._tcp SRV     0 0 3689 flexs-MacBook-Pro.local. ; Replace with unicast FQDN of target host
flex’s\032MacBook\032Pro\032Library_PW._daap._tcp TXT     "txtvers=1" "Version=196621" "MID=0x712648C4C2B6BBB" "Database ID=6658B926016842AE" "Machine ID=5973179E8FBB" "dmv=131085" "OSsi=0x1F5" "Media Kinds Shared=1025" "iTSh Version=196622" "Password=1" "Machine Name=flex’s MacBook Pro Library"

_daap._tcp                                      PTR     flex’s\032iMac\032Library_PW._daap._tcp
flex’s\032iMac\032Library_PW._daap._tcp       SRV     0 0 3689 Fleischmanns-iMac.local. ; Replace with unicast FQDN of target host
flex’s\032iMac\032Library_PW._daap._tcp       TXT     "txtvers=1" "Version=196621" "MID=0x23C2D711F8740F6D" "Database ID=7C219A41B9C26D48" "Machine ID=B2483356245F" "dmv=131085" "OSsi=0x1F8" "Media Kinds Shared=1048655" "iTSh Version=196622" "Password=1" "Machine Name=flex’s iMac Library"
```

Ebből az látszik, hogy nekem a futtatás pillanatában épp három ilyen forrásom volt aktív. 

Ezen lista alapján és a gépek, eszközök IP címének ismeretében, amikor nem vagyok otthon, akkor a VPN kapcsolat felépítése utána kiadva mondjuk ezt a parancsot:

<pre class="terminal">dns-sd -P "Music on server" _daap._tcp local 3689 BLACKHOLE.fleischmann.local. \
    192.168.1.2 "Password=false" "Version=196610" "iTSh Version=131073" "mtd-version=0.2.4.1" "Machine Name=MUZAX" "Machine ID=" "Database ID=" "txtvers=1"</pre>

azonnal elérhetővé is válik a kiszemelt (jelen példában ez épp 1 Synology NAS) eszközünk az iTunes-ban és már lehet is hallgatni az ott megosztott zenéket.