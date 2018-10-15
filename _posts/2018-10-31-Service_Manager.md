---
layout:   post
title:    MicroFocus / HPE / HP Service Manager  
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [microFocus, hpe, hp, service manager, sm, how to]
---

Na akkor fussunk is neki az alapoknak!

## A tesztkörnyezet

A tesztrendszer SM verziója: **v9.60**, operációs rendszerei:
<pre class="terminal">
Linux hpsm 3.10.0-862.11.6.el7.x86_64 #1 SMP Tue Aug 14 21:49:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
</pre>
<pre class="terminal">
Linux oracle01.eg.office 4.1.12-124.18.6.el7uek.x86_64 #2 SMP Wed Aug 15 19:12:26 PDT 2018 x86_64 x86_64 x86_64 GNU/Linux
</pre>

A tesztrendszer WEB felületét itt lehet elérni: [http://mysmdev:8080/sm/index.do?lang=en](http://mysmdev:8080/sm/index.do?lang=en) (természetesen ez a cím csak nálunk házon belül működik!, de a lényeg a link vége.)

### SM elindítása

#### 1. Oracle DB

<pre class="terminal"><strong style="color: #00FF00;">[oracle@oracle01 ~]$</strong> lsnrctl start

LSNRCTL for Linux: Version 12.1.0.2.0 - Production on 08-OCT-2018 10:30:05

Copyright (c) 1991, 2014, Oracle.  All rights reserved.

Starting /u01/app/oracle/product/12.1.0/dbhome_1//bin/tnslsnr: please wait...

TNSLSNR for Linux: Version 12.1.0.2.0 - Production
System parameter file is /u01/app/oracle/product/12.1.0/dbhome_1/network/admin/listener.ora
Log messages written to /u01/app/oracle/diag/tnslsnr/oracle01/listener/alert/log.xml
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=localhost)(PORT=1521)))
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC1521)))

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=oracle01)(PORT=1521)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 12.1.0.2.0 - Production
Start Date                08-OCT-2018 10:30:07
Uptime                    0 days 0 hr. 0 min. 1 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Listener Parameter File   /u01/app/oracle/product/12.1.0/dbhome_1/network/admin/listener.ora
Listener Log File         /u01/app/oracle/diag/tnslsnr/oracle01/listener/alert/log.xml
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=localhost)(PORT=1521)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC1521)))
The listener supports no services
The command completed successfully</pre>

<pre class="terminal"><strong style="color: #00FF00;">[oracle@oracle01 ~]$</strong> dbstart
ORACLE_HOME_LISTNER is not SET, unable to auto-start Oracle Net Listener
Usage: /u01/app/oracle/product/12.1.0/dbhome_1//bin/dbstart ORACLE_HOME
Processing Database instance "hpsm": log file /u01/app/oracle/product/12.1.0/dbhome_1/startup.log
</pre>

#### 2. Service Manager

<pre class="terminal"><strong style="color: #00FF00;">[root@hpsm ~]#</strong> su - hpsm
Last login: Fri Oct  5 10:52:34 CEST 2018 on pts/0
<strong style="color: #00FF00;">[hpsm@hpsm ~]$</strong> cd /opt/MicroFocus/ServiceManager9.60/Server/RUN/
<strong style="color: #00FF00;">[hpsm@hpsm RUN]$</strong> ./smstart
Starting sm
Starting sm system.start</pre>

Az SM logja az: /opt/MicroFocus/ServiceManager9.60/Server/logs/ könyvtárban található **sm.log** néven.

#### 3. Alkalmazás szerver 

Ha ez nem indulna magától, akkor:

<pre class="terminal"><strong style="color: #00FF00;">[root@hpsm ~]#</strong> systemctl start tomcat
<strong style="color: #00FF00;">[root@hpsm ~]#</strong> systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
   Loaded: loaded (/etc/systemd/system/tomcat.service; enabled; vendor preset: disabled)
   Active: <strong style="color: #00FF00;">active (running)</strong> since Mon 2018-10-08 10:15:38 CEST; 1 day 23h ago
  Process: 1045 ExecStart=/opt/tomcat/bin/startup.sh (code=exited, status=0/SUCCESS)
 Main PID: 1091 (java)
   CGroup: /system.slice/tomcat.service
           └─1091 /usr/java/jdk1.8.0_181-amd64//bin/java -Djava.util.logging.config.file=/opt/tomcat/conf/logging.properties -Djava.util.logging.manage...

Oct 08 10:15:38 hpsm systemd[1]: Starting Apache Tomcat Web Application Container...
Oct 08 10:15:38 hpsm startup.sh[1045]: Existing PID file found during start.
Oct 08 10:15:38 hpsm startup.sh[1045]: Removing/clearing stale PID file.
Oct 08 10:15:38 hpsm startup.sh[1045]: Tomcat started.
Oct 08 10:15:38 hpsm systemd[1]: Started Apache Tomcat Web Application Container.
</pre>

#### 4. Bejelentkező képernyő

Ha minden jól ment, akkor a következő képernyő fogad majd az előző lépések után, ahol be lehet jelentkezni a Service Manager-be.

<center><img class="shadow" src="images/sm/login.png" style="width: 60%;"></center>

# Service Manager

## Alap dolgok

### Session TimeOut

**Menu Navigation:** System Administration - Ongoing Maintenance - System - Start Inactivity Timer

### Kontextus-érzékeny segítség bekapcsolása

Ezzel az opcióval Ctrl-h-t nyomja egy mezőn, megkajuk az aktuális form, tábla és mező nevét.

<img class="shadow" src="images/sm/sm_client_windows_preferences1.png">

### Ikonok

A munkafolyamatokhoz felhasználható ikonok a **/opt/tomcat/webapps/sm/images/obj16** könyvtárban találhatóak.

### Új power user létrehozása

**Menu Navigation:** System Administration - Ongoing Maintenance > User Quick Add Utility menü segítségével készíthetünk:

<img class="shadow" src="images/sm/poweruser1.png">

<img class="shadow" src="images/sm/poweruser2.png">

### Új menük készítése + hozzá parancsok

### Hogyan kell megtalálni egy menüt

### Hogyan kell létrezhoni

### $file használata

- $file - Format Control
- $File - Links
- $L.file - minden más
- $L.filed - Display App.

Részletek találhatóak a következő [link](https://ernestodisanto.wordpress.com/2015/10/30/hpsm-current-file-variable-in-rad/)-en.

### Variables

- $G. $lo Globális változók
- $L. lokális változók
- minden más thread változó

### Forms Designer

Hogyan készítsünk olyan Form-okat, amivel meg lehet könnyen találni a Globalists neveket vagy a Mezőneveket?

#### Globális lista nevének megkeresése

Amit tudni fog az az, hogy meg lehet keresni egy globális lista változója vagy a változó megjelenítési változója alapján a lista nevét, illetve ezek összes kombinációja megadása esetén a hiányzókat. Ez jó segítség lesz a Process Designer-ben készített Workflow-khoz. 

Ehhez kell majd nekünk:

- egy form (fd, _flex.global.list.entry), ez lesz végül majd a kereső és a megjelenítő form is, amikor ilyet keresünk: _flex.global.list.entry

<img class="shadow" src="images/sm/fd_globallists_form.png">

- egy qbe form (fd, _flex.globallist.qbe.g) (ennek most sok még sok jelentősége nincs, mert csak a PopUp részeken van/lesz jelentősége)

majd ezeken kívül kell még:

- egy format control (fc, _flex.global.list.entry) is, ami a form-unkon ki fog tölteni egy mezőt($flex.hidden thread változó), és ha az én form-omat hasznájuk a kereséskor akkor, egy display option (Object Definition - Default State Definition - Display Application Screen Definition) ki fogja majd értékelni és az alapján a keresési eredményt majd ugyanebben form-ban megjeleníteni a gyári helyett.

<img class="shadow" src="images/sm/fd_globallists_fc1.png">

<img class="shadow" src="images/sm/fd_globallists_fc2.png">

<img class="shadow" src="images/sm/fd_globallists_object.png">

<img class="shadow" src="images/sm/fd_globallists_state.png">

<img class="shadow" src="images/sm/fd_globallists_display_screen.png">

```
// $L.format="_flex.global.list.entry"

if (nullsub($flex.hidden, "X")~="OK") then ($L.format="apm.global.list.entry") else ($L.format="_flex.global.list.entry")
```

és talán ez a téma összességében ennyi is.

<img class="shadow" src="images/sm/fd_globallists_final_form.png">

#### Datadict-ből a mezőnevek kikeresése

Ezt már egy kicsit tovább sikerült csavarni. Ehhez kelleni fog majd egy segédtábla (types) is, amibe felvittem a Service Manager-es típusokat is és a keresés után így ki tudja írni nem csak a nevét, de még a mező típusát is.

**Menu Navigation:** System Definition - Tables

<img class="shadow" src="images/sm/fd_datadict_types1.png">

<img class="shadow" src="images/sm/fd_datadict_types2.png">

<img class="shadow" src="images/sm/fd_datadict_types3.png">

És itt lesz egy gomb, ami a lekérdezett tömbökben és a típusok között is tud majd keresni. A gomb egy Display Option mögött van és ott hívódik hozzá egy a Script Library-ben lévő JavaScript function: "lib._flex.searchCaption();" A lényeg a következő:

<img class="shadow" src="images/sm/fd_datadict_form.png">

<img class="shadow" src="images/sm/fd_datadict_object.png">

<img class="shadow" src="images/sm/fd_datadict_state.png">

<img class="shadow" src="images/sm/fd_datadict_display_screen.png">

<img class="shadow" src="images/sm/fd_datadict_dispaly_option1.png">

<img class="shadow" src="images/sm/fd_datadict_script_library.png">

```javascript
function searchCaption () {
	for ( var i = 0; i < vars["$L.file"].fields.length(); i++ ) {
	
		if ( vars["$L.file"].fields[i] == vars.$flex_field ) {
			vars.$flex_caption = vars["$L.file"].captions[i];
			vars.$type = getTypeName( vars["$L.file"].types[i] ); 
			break;
		}
		else {
			vars.$flex_caption = "NOT FOUND!!!";
		}
	}
}

function getTypeName( typex ) {
	var types = new SCFile( "types" );
	
	print ( "Ok" );
	
	var rc = types.doSelect( "representation="+ typex );

	if ( rc == RC_SUCCESS ) {
	  print( "Success. found." );
	  return types.name;
	}
	else {
		print( "Could not find type!" + RCtoString( rc ) );
		return null;
	}
}
```

Próbáltam még erre a form-ra feltenni egy olyan gombot is, ami az SM licenceit mutatja meg egy Text Box-ban. 

<img class="shadow" src="images/sm/fd_datadict_display_option2.png">

```javascript
function getLicenseInfo() {
	var license = system.functions.get_module_license();

 	for ( var i in license ) {
 		var module = system.functions.strraw( license[i], "," );
 		var module1 = module.split( "," );

		 if ( module1[0] == "Self Service Ticketing" ) {
		 	print( module1[0] + " " + module1[2] + "(Unlimited)" );
		 }
		 else {
		 	print( module1[0] + " Named License " + module1[1] + "(" + module1[3] + ")" + " Float License " + module1[2] + "(" + module1[4] + ")" );
		 	vars.$flexdebug += module1[0] + " Named License " + module1[1] + "(" + module1[3] + ")" + " Float License " + module1[2] + "(" + module1[4] + ")" + String.fromCharCode(13);
		 }
 	}
}
```

## Process Designer

Best practices [link](https://docs.microfocus.com/SM/9.52/Hybrid/Content/PD_tailoring_BPG/Process_Designer_Basic_Concepts.htm)

**Menu Navigation:** Tailoring - Process Designer

### Fázisok ás átmenetek létrehozásának trükkjei

**Menu Navigation:** Tailoring - Process Designer - Workflows

1. érdemes a fázisokat egyből létrehozni és azonnal elnevezni 
2. figyelni kell, hogy a átmenet parancs nevének megadásánál felül fogja írni a mögötte lévé scmessage rekordot is!

<img class="shadow" src="images/sm/workflow_rule_naming.png" style="width: 30%;">

### Alapértékek és kitöltések ellenőrzése [Rule Sets]

**Menu Navigation:** Tailoring - Process Designer - Rule Sets

<img class="shadow" src="images/sm/workflow_rule_set_default.png">

<img class="shadow" src="images/sm/workflow_rule_set_via_javascript1.png">

<img class="shadow" src="images/sm/workflow_rule_set_via_javascript2.png">

<img class="shadow" src="images/sm/workflow_rule_set_mandatory_default.png">

value="Unplanned Change Detection"
value="Rrrrisk ass"

A mezők nevénél nem magát a mezőnek a nevét kell megadni (amit a vastag kliensben a mezőt kijelölve és Ctrl-h nyomva tudunk megkapni, ha a Window - Preferences menüpontban a Service Manager almenüben az Appearance részében a "Show context-sensitive help debug information" opció be van kapcsolva)

<img class="shadow" src="images/sm/sm_client_windows_preferences1.png">

, hanem a Data Policy-ben lévő Caption nevét kell megadni a mezőhivatkozásoknál.

### Lista ellenőrzése egy globális lista alapján

<img class="shadow" src="images/sm/workflow_rule_set_validate_against_list.png">

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

**Menu Navigation:** Change management - Configuration - Change Categories