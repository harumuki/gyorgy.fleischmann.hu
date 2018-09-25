---
layout:   post
title:    How to install IBM TSM BA client on a Synology NAS  
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [ibm, tivoli storage manager, tsm, spectrum proetect, sp, install, how to]
---

<pre class="terminal">
<strong style="color: #00FF00;">root@BLACKHOLE:/</strong># ls -lh
total 115M
-rw-rw-r-- 1 flex flex 115M Sep 24 10:22 baclient.tar.gz

root@BLACKHOLE:~#tree
.
├── opt
│   └── tivoli
│       └── tsm
│           └── client
│               ├── api
│               │   └── bin64
│               │       ├── dsmcert
│               │       ├── dsm.opt.smp
│               │       ├── dsm.sys.smp
│               │       ├── EN_US
│               │       │   ├── dscjres.txt
│               │       │   ├── dsmc.hlp
│               │       │   ├── dsmclientV3.cat
│               │       │   ├── dsmig.hlp
│               │       │   ├── tsmhelp.jar
│               │       │   ├── uil_nls.jar
│               │       │   └── wchelp.htl
│               │       ├── libApiTSM64.so
│               │       ├── libcrypto.so.1.0.2
│               │       ├── libdmapi.so
│               │       ├── libgpfs.so
│               │       ├── libssl.so.1.0.2
│               │       ├── libTsmViSdkAPI.so -> libTsmViSdk.so
│               │       ├── libTsmViSdk.so
│               │       ├── libtsmxerces-c.so.28.0
│               │       ├── libtsmxerces-depdom.so.28.0
│               │       ├── libVMcrypto.so -> libcrypto.so.1.0.2
│               │       ├── libVMssl.so -> libssl.so.1.0.2
│               │       ├── libxmlutil-8.1.6.0.so
│               │       └── sample
│               │           ├── callbuff.c
│               │           ├── callevnt.c
│               │           ├── callhold.c
│               │           ├── callmt1.c
│               │           ├── callmt2.c
│               │           ├── callret.c
│               │           ├── dapibkup.c
│               │           ├── dapidata.h
│               │           ├── dapiinit.c
│               │           ├── dapint64.c
│               │           ├── dapint64.h
│               │           ├── dapipref.c
│               │           ├── dapiproc.c
│               │           ├── dapiproc.h
│               │           ├── dapipw.c
│               │           ├── dapiqry.c
│               │           ├── dapirc.c
│               │           ├── dapismp.c
│               │           ├── dapitype.h
│               │           ├── dapiutil.c
│               │           ├── dapiutil.h
│               │           ├── dpsthread.c
│               │           ├── dpsthread.h
│               │           ├── dsmapifp.h
│               │           ├── dsmapips.h
│               │           ├── dsmapipw.c
│               │           ├── dsmapitd.h
│               │           ├── dsmgrp.c
│               │           ├── dsmrc.h
│               │           ├── makesmp64.linux86
│               │           ├── release.h
│               │           ├── tsmapifp.h
│               │           └── tsmapitd.h
│               └── ba
│                   └── bin
│                       ├── commonFunctions
│                       ├── configFile
│                       ├── dsmadmc
│                       ├── dsmagent
│                       ├── dsmc
│                       ├── dsmcad
│                       ├── dsmcad.service
│                       ├── dsmcert
│                       ├── dsmj
│                       ├── dsm.jar
│                       ├── dsm.opt.smp
│                       ├── dsm_pref.jar
│                       ├── dsmswitch
│                       ├── dsm.sys.smp
│                       ├── dsmtrace
│                       ├── dsmutillnx
│                       ├── EN_US
│                       │   ├── dscjres.txt
│                       │   ├── dsmc.hlp
│                       │   ├── dsmclientV3.cat
│                       │   ├── dsmig.hlp
│                       │   ├── tsmhelp.jar
│                       │   ├── uil_nls.jar
│                       │   └── wchelp.htl
│                       ├── exposeFastBackSnapshot.sh
│                       ├── favicon.ico
│                       ├── getFastBackSnapshots.sh
│                       ├── httpagent.jar
│                       ├── images
│                       │   └── wchelp.htl
│                       ├── iscsiMount.sh
│                       ├── jdom.jar
│                       ├── jh.jar
│                       ├── libTsmViSdkAPI.so -> libTsmViSdk.so
│                       ├── libTsmViSdk.so
│                       ├── nasdcm.lic
│                       ├── plugins
│                       │   ├── libPiIMG.so
│                       │   ├── libPiSNAP.so
│                       │   ├── libPiVcloudJNI.so
│                       │   ├── libPiVcloudSuiteJNI.so
│                       │   ├── vcloud
│                       │   │   ├── piVcloudJwrapper.jar
│                       │   │   └── sdk
│                       │   │       ├── amqp-client-2.8.6.jar
│                       │   │       ├── commons-codec-1.6.jar
│                       │   │       ├── commons-logging-1.1.1.jar
│                       │   │       ├── httpclient-4.2.jar
│                       │   │       ├── httpcore-4.2.jar
│                       │   │       ├── rest-api-schemas-5.5.0.jar
│                       │   │       └── vcloud-java-sdk-5.5.0.jar
│                       │   └── vcloudsuite
│                       │       ├── piVcloudSuiteJwrapper.jar
│                       │       └── sdk
│                       │           ├── commons-beanutils-1.8.3.jar
│                       │           ├── commons-cli-1.3.1.jar
│                       │           ├── commons-codec-1.9.jar
│                       │           ├── commons-configuration-1.10.jar
│                       │           ├── commons-lang-2.5.jar
│                       │           ├── commons-logging-1.2.jar
│                       │           ├── httpasyncclient-4.1.jar
│                       │           ├── httpclient-4.5.1.jar
│                       │           ├── httpcore-4.4.3.jar
│                       │           ├── httpcore-nio-4.4.3.jar
│                       │           ├── jackson-core-asl-1.9.2.jar
│                       │           ├── jackson-mapper-asl-1.9.2.jar
│                       │           ├── log4j-1.2.17.jar
│                       │           ├── log4j.properties
│                       │           ├── logging.properties
│                       │           ├── slf4j-api-1.6.6.jar
│                       │           ├── slf4j-log4j12-1.6.6.jar
│                       │           ├── ssoclient.jar
│                       │           ├── vapi-authentication-2.5.0.jar
│                       │           ├── vapi-runtime-2.5.0.jar
│                       │           ├── vapi-samltoken-2.5.0.jar
│                       │           ├── vim25.jar
│                       │           ├── vsphereautomation-client-sdk-6.5.0.jar
│                       │           └── vsphereautomation-lookupservice-6.5.0.jar
│                       ├── rc.dsmcad
│                       ├── r_FastBackShell.sh
│                       ├── uil.jar
│                       ├── unMountForTSM.sh
│                       ├── vmscan
│                       │   ├── BackupMon.exe
│                       │   ├── CheckEnv.exe
│                       │   └── DeleteVMScanFiles.bat
│                       ├── vmtsmvss
│                       │   ├── BackupMon.exe
│                       │   ├── CheckEnv.exe
│                       │   ├── DeleteACMFiles.bat
│                       │   ├── DummyBAProxy.exe
│                       │   ├── ProxyBAClient.exe
│                       │   ├── ProxyBAServer.exe
│                       │   ├── register_app.vbs
│                       │   ├── TsmMSSqlLogTruncation.bat
│                       │   └── TsmVmwareDpVSS.dll
│                       ├── xercesImpl_2_2_1.jar
│                       └── xmlParserAPIs_2_2_1.jar
└── usr
    ├── bin
    │   ├── dsmadmc -> ../../opt/tivoli/tsm/client/ba/bin/dsmadmc
    │   ├── dsmagent -> ../../opt/tivoli/tsm/client/ba/bin/dsmagent
    │   ├── dsmc -> ../../opt/tivoli/tsm/client/ba/bin/dsmc
    │   ├── dsmcad -> ../../opt/tivoli/tsm/client/ba/bin/dsmcad
    │   ├── dsmcert -> ../../opt/tivoli/tsm/client/ba/bin/dsmcert
    │   ├── dsmj -> ../../opt/tivoli/tsm/client/ba/bin/dsmj
    │   ├── dsmswitch -> ../../opt/tivoli/tsm/client/ba/bin/dsmswitch
    │   └── dsmtrace -> ../../opt/tivoli/tsm/client/ba/bin/dsmtrace
    ├── lib64
    │   ├── libApiTSM64.so -> ../../opt/tivoli/tsm/client/api/bin64/libApiTSM64.so
    │   ├── libtsmxerces-c.so.28 -> ../../opt/tivoli/tsm/client/api/bin64/libtsmxerces-c.so.28.0
    │   ├── libtsmxerces-depdom.so.28 -> ../../opt/tivoli/tsm/client/api/bin64/libtsmxerces-depdom.so.28.0
    │   └── libxmlutil-8.1.6.0.so -> ../../opt/tivoli/tsm/client/api/bin64/libxmlutil-8.1.6.0.so
    └── local
        └── ibm
            └── gsk8_64
                ├── bin
                │   ├── gsk8capicmd_64
                │   └── gsk8ver_64
                ├── copyright
                ├── docs
                ├── inc
                ├── lib64
                │   ├── C
                │   │   └── icc
                │   │       ├── icclib
                │   │       │   ├── ICCSIG.txt
                │   │       │   └── libicclib084.so
                │   │       └── ReadMe.txt
                │   ├── libgsk8acmeidup_64.so
                │   ├── libgsk8cms_64.so
                │   ├── libgsk8dbfl_64.so
                │   ├── libgsk8drld_64.so
                │   ├── libgsk8iccs_64.so
                │   ├── libgsk8kicc_64.so
                │   ├── libgsk8km2_64.so
                │   ├── libgsk8km_64.so
                │   ├── libgsk8ldap_64.so
                │   ├── libgsk8p11_64.so
                │   ├── libgsk8ssl_64.so
                │   ├── libgsk8sys_64.so
                │   ├── libgsk8valn_64.so
                │   └── N
                │       └── icc
                │           ├── icclib
                │           │   ├── ICCSIG.txt
                │           │   └── libicclib085.so
                │           └── ReadMe.txt
                └── ReadMe.txt
</pre>

## stop scheduler / dsmcad

stop dsmcad

```
start dsmcad
```
<pre class="terminal"><strong style="color: #00FF00;">root@BLACKHOLE:/</strong># stop dsmcad
dsmcad stop/waiting</pre>

## restart scheduler / dsmcad

```
start dsmcad
```
<pre class="terminal"><strong style="color: #00FF00;">root@BLACKHOLE:/</strong># start dsmcad
dsmcad start/running, process 13683</pre>

```
dsmc q sess
```
<pre class="terminal"><strong style="color: #00FF00;">root@BLACKHOLE:/</strong># dsmc q sess
    
IBM Spectrum Protect
Command Line Backup-Archive Client Interface
  Client Version 8, Release 1, Level 6.0
  Client date/time: 09/24/2018 10:33:00
(c) Copyright by IBM Corporation and other(s) 1990, 2018. All Rights Reserved.

Node Name: BLACKHOLE
Session established with server CLOUDTSM1: Linux/x86_64
  Server Version 8, Release 1, Level 4.000
  Server date/time: 09/24/2018 10:33:00  Last access: 09/24/2018 10:31:34

IBM Spectrum Protect Server Connection Information

Home Server Name........: SERVER_A
Server Type.............: Linux/x86_64
Archive Retain Protect..: "No"
Server Version..........: Ver. 8, Rel. 1, Lev. 4.0
Last Access Date........: 09/24/2018 10:31:34
Delete Backup Files.....: "No"
Delete Archive Files....: "Yes"
Deduplication...........: "Server Only"

Node Name...............: BLACKHOLE
User Name...............: root

SSL Information.........: TLSv1.2 TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384

Secondary Server Information
Not configured for failover</pre>