---
layout: post
status: publish
published: true
title: Disable TSM server activities
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 200
wordpress_url: http://fleischmann.hu/wp/?p=200
date: '2010-02-24 15:13:10 +0100'
date_gmt: '2010-02-24 14:13:10 +0100'
categories:
- IBM Tivoli Storage Manager
tags:
- TSM
- IBM Tivoli Storage Manager
comments: []
---
<p>Add:<br />
--- CUT---<br />
<strong><tt><br />
 Disablescheds yes<br />
 NOMIGRRECL<br />
 EXPINTERVAL 0<br />
</tt></strong><br />
--- CUT---<br />
to dsmserv.opt</p>
