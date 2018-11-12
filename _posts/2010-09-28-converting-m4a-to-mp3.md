---
layout: post
status: publish
published: true
title: Converting .m4a to .mp3
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 478
wordpress_url: http://fleischmann.hu/wp/?p=478
date: '2010-09-28 10:33:06 +0200'
date_gmt: '2010-09-28 09:33:06 +0200'
categories:
- Mac
tags:
- knowledge
- Mac
comments: []
---
<p>Use online converter like: <a href="http://media-convert.com/">http://media-convert.com/</a> or </p>
<pre><font color="#00FF00" style="font-size:14px">sudo port install mplayer-devel lame

for i in *.m4a
do
  mplayer -ao pcm:file="$i.wav" "$i"
  lame -h -b 192 "$i.wav" "$i.mp3"
done</font></pre>
<p>Source: <a href="http://www.linuxquestions.org/questions/linux-general-1/converting-m4a-to-mp3-170553/">http://www.linuxquestions.org/</a></p>
<p><a href='http://fleischmann.hu/wp/store/2010/09/20100926-085507.mp3'>20100926 085507</a></p>
