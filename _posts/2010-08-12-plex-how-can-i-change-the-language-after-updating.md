---
layout: post
status: publish
published: true
title: 'PLEX: How can I change the language after updating?'
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 401
wordpress_url: http://fleischmann.hu/wp/?p=401
date: '2010-08-12 18:47:00 +0200'
date_gmt: '2010-08-12 17:47:00 +0200'
categories:
- Mac
tags:
- command line
- knowledge
- Mac
comments: []
---
<p><a href="http://wiki.plexapp.com/index.php/Advanced_Settings">Advanced settings</a></p>
<p>Edit ~/Library/Application Support/Plex/userdata/advancedsettings.xml (create it if it doesn't exist) and add a setting for language and/or units like this:</p>
<pre><?xml version="1.0"?>
<advancedsettings>
  <language>us</language> <!-- Use ISO language code -->
  <units>metric</units>
</advancedsettings></pre>
