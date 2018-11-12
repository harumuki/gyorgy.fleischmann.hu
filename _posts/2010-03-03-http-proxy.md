---
layout: post
status: publish
published: true
title: HTTP proxy curl
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 206
wordpress_url: http://fleischmann.hu/wp/?p=206
date: '2010-03-03 12:58:03 +0100'
date_gmt: '2010-03-03 11:58:03 +0100'
categories:
- knowledge
tags:
- command line
- knowledge
- UNIX
- curl
comments: []
---
<p>curl --proxy-user DOMAIN\\username:$PASSWD  --proxy proxy:8080 --proxy-ntlm --disable-epsv --disable-eprt -Q 'prot p' ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.tar.bz2 -o linux-2.6.33.tar.bz2</p>
