---
layout: post
status: publish
published: true
title: 'IC70791: CONTENT DATA RESTORATION OF A STUB FILE DURING A RECALL OPERATION
  MAY CRASH THE WINDOWS SYSTEM BY CAUSING A BLUE SCREEN.'
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 414
wordpress_url: http://fleischmann.hu/wp/?p=414
date: '2010-08-31 10:31:19 +0200'
date_gmt: '2010-08-31 09:31:19 +0200'
categories:
- IBM Tivoli Storage Manager
tags:
- TSM
- IBM Tivoli Storage Manager
- knowledge
- IBM
- MS Windows
- HSM
- Hierarchical Storage Management
comments: []
---
<p><a href="http://www-01.ibm.com/support/docview.wss?uid=swg1IC70791&myns=swgtiv&mynp=OCSSATMW&mync=R">IC70791: CONTENT DATA RESTORATION OF A STUB FILE DURING A RECALL OPERATION MAY CRASH THE WINDOWS SYSTEM BY CAUSING A BLUE SCREEN.</a></p>
<pre>If one of the following operations during file restauration fail
s, a bluescreen (BSOD) is caused by the HSM for Windows driver,
ithsmdrv.sys :

- File information query for the stub file to restore fails
- Stub file is compressed and decompression fails
- Opening the temporary content data file fails

As a consequenceof these error cases, the driver accesses stack
memory, that it did not allocate and causes the Windows system
to crash with a bluescreen.
</pre>
