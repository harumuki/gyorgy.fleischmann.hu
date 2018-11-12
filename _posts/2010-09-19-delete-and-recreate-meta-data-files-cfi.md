---
layout: post
status: publish
published: true
title: Delete and recreate HSM meta data files (Complete File Index, CFI)
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 463
wordpress_url: http://fleischmann.hu/wp/?p=463
date: '2010-09-19 08:36:25 +0200'
date_gmt: '2010-09-19 07:36:25 +0200'
categories:
- IBM Tivoli Storage Manager
- knowledge
tags:
- IBM Tivoli Storage Manager
- knowledge
- Linux
- IBM
- AIX
- HSM
- Space Management
comments: []
---
<pre><font color="#00FF00" style="font-size:14px">dsmscoutd stop
rm -rf /hsm_managed_file_system_spec/.SpaceMan/metadata
dsmscoutd start</font></pre>
<p>Source: <a href="http://adsm.org/forum/showthread.php?14859-DSMSCOUTD-problems">DSMSCOUTD problems</a></p>
