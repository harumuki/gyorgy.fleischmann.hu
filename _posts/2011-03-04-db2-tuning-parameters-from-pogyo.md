---
layout: post
status: publish
published: true
title: DB2 tuning parameters from PoGy&Atilde;&para;
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 613
wordpress_url: http://fleischmann.hu/wp/?p=613
date: '2011-03-04 14:07:12 +0100'
date_gmt: '2011-03-04 13:07:12 +0100'
categories:
- IBM Tivoli Storage Manager
- knowledge
tags:
- IBM Tivoli Storage Manager
- knowledge
- DB2
- IBM
- v6.x
- fromPoGy&Atilde;&para;
comments: []
---
<p>TSM 6.2 DB2 tunning and sizing,</p>
<p>db2 connect to XXX<br />
db2 "select * from syscat.bufferpools" -<br />
Ennek az eredm&Atilde;&copy;ny&Atilde;&copy;vel kell FellegZ-t keresni....</p>
<p>db2update db cfg for XXX using softmax 100-200<br />
db2update db cfg for XXX using logprimary 2<br />
db2update db cfg for XXX using logsecond 200-250<br />
db2update db cfg for XXX using logfilsiz 1024 v 4096<br />
db2stop<br />
db2start</p>
