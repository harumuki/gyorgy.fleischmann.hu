---
layout: post
status: publish
published: true
title: How can I rename multiple files using wildcards?
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 592
wordpress_url: http://fleischmann.hu/wp/?p=592
date: '2011-01-31 20:32:16 +0100'
date_gmt: '2011-01-31 19:32:16 +0100'
categories:
- knowledge
- Linux
tags:
- knowledge
- Linux
comments: []
---
<p>for i in `ls -1 *.JPE`; do mv $i ${i/JPE/JPG}; done</p>
