---
layout: post
status: publish
published: true
title: AIX ramdisk
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 524
wordpress_url: http://fleischmann.hu/wp/?p=524
date: '2010-10-21 13:56:51 +0200'
date_gmt: '2010-10-21 12:56:51 +0200'
categories:
- knowledge
- AIX
tags:
- command line
- knowledge
- AIX
comments: []
---
<pre>mkramdisk 1G
ls -l /dev | grep ram => ramdiskX
/sbin/helpers/jfs2/mkfs -V jfs2 /dev/ramdiskX
mkdir /ramdiskX
mount -V jfs2 -o log=NULL /dev/ramdiskx /ramdiskX</pre>
