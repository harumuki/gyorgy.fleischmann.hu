---
layout: post
status: publish
published: true
title: Repair flash disk on OS X
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 423
wordpress_url: http://fleischmann.hu/wp/?p=423
date: '2010-09-07 17:12:28 +0200'
date_gmt: '2010-09-07 16:12:28 +0200'
categories:
- Mac
tags:
- Mac
comments: []
---
<pre><font color="#00FF00" style="font-size:14px">macbook:~ flex$ <strong>sudo port selfupdate</strong>
Password:
--->  Updating the ports tree
--->  Updating MacPorts base sources using rsync
MacPorts base version 1.8.2 installed,
MacPorts base version 1.9.1 downloaded.
--->  MacPorts base is outdated, installing new version 1.9.1
Installing new MacPorts release in /opt/local as root:admin; permissions 0755; Tcl-Package in /Library/Tcl


The ports tree has been updated. To upgrade your installed ports, you should run
  port upgrade outdated
macbook:~ flex$ <strong>sudo port install testdisk</strong>
--->  Computing dependencies for jpeg
--->  Fetching jpeg
--->  Attempting to fetch jpegsrc.v8b.tar.gz from http://lil.fr.distfiles.macports.org/jpeg
--->  Verifying checksum(s) for jpeg
--->  Extracting jpeg
--->  Configuring jpeg
--->  Building jpeg
--->  Staging jpeg into destroot
--->  Computing dependencies for jpeg
--->  Installing jpeg @8b_0+universal
--->  Deactivating jpeg @8a_0+universal
--->  Activating jpeg @8b_0+universal
--->  Cleaning jpeg
--->  Computing dependencies for openssl
--->  Fetching openssl
--->  Attempting to fetch openssl-1.0.0a.tar.gz from http://www.openssl.org/source/
--->  Verifying checksum(s) for openssl
--->  Extracting openssl
--->  Applying patches to openssl
--->  Configuring openssl
--->  Building openssl
--->  Staging openssl into destroot
--->  Computing dependencies for openssl
--->  Installing openssl @1.0.0a_0
--->  Deactivating openssl @0.9.8n_0+darwin
--->  Activating openssl @1.0.0a_0
--->  Cleaning openssl
--->  Computing dependencies for testdisk
--->  Dependencies to be installed: e2fsprogs ossp-uuid libewf ntfsprogs
--->  Fetching ossp-uuid
--->  Attempting to fetch uuid-1.6.2.tar.gz from ftp://ftp.ossp.org/pkg/lib/uuid/
--->  Verifying checksum(s) for ossp-uuid
--->  Extracting ossp-uuid
--->  Applying patches to ossp-uuid
--->  Configuring ossp-uuid
--->  Building ossp-uuid
--->  Staging ossp-uuid into destroot
--->  Installing ossp-uuid @1.6.2_0
--->  Activating ossp-uuid @1.6.2_0
--->  Cleaning ossp-uuid
--->  Fetching e2fsprogs
--->  Attempting to fetch e2fsprogs-1.41.12.tar.gz from http://ovh.dl.sourceforge.net/e2fsprogs
--->  Verifying checksum(s) for e2fsprogs
--->  Extracting e2fsprogs
--->  Applying patches to e2fsprogs
--->  Configuring e2fsprogs
--->  Building e2fsprogs
--->  Staging e2fsprogs into destroot
--->  Installing e2fsprogs @1.41.12_0
--->  Activating e2fsprogs @1.41.12_0
--->  Cleaning e2fsprogs
--->  Fetching libewf
--->  Attempting to fetch libewf-20100226.tar.gz from http://ignum.dl.sourceforge.net/libewf
--->  Verifying checksum(s) for libewf
--->  Extracting libewf
--->  Configuring libewf
--->  Building libewf
--->  Staging libewf into destroot
--->  Installing libewf @20100226_0
--->  Activating libewf @20100226_0
--->  Cleaning libewf
--->  Fetching ntfsprogs
--->  Attempting to fetch ntfsprogs-2.0.0.tar.gz from http://ignum.dl.sourceforge.net/linux-ntfs
--->  Verifying checksum(s) for ntfsprogs
--->  Extracting ntfsprogs
--->  Configuring ntfsprogs
--->  Building ntfsprogs
--->  Staging ntfsprogs into destroot
--->  Installing ntfsprogs @2.0.0_0
--->  Activating ntfsprogs @2.0.0_0
--->  Cleaning ntfsprogs
--->  Fetching testdisk
--->  Attempting to fetch testdisk-6.11.tar.bz2 from http://lil.fr.distfiles.macports.org/testdisk
--->  Verifying checksum(s) for testdisk
--->  Extracting testdisk
--->  Applying patches to testdisk
--->  Configuring testdisk
--->  Building testdisk
--->  Staging testdisk into destroot
--->  Installing testdisk @6.11_5
--->  Activating testdisk @6.11_5
--->  Cleaning testdisk
macbook:~ flex$ 
</font></pre>
<p><a href="http://www.debian-administration.org/articles/420">Recovering from file system corruption using TestDisk</a></p>
