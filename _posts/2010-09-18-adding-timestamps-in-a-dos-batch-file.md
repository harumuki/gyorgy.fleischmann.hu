---
layout: post
status: publish
published: true
title: Adding timestamps in a DOS batch file
author:
  display_name: flex
  login: flex
  email: gyorgy@fleischmann.hu
  url: http://www.fleischmann.hu/
author_login: flex
author_email: gyorgy@fleischmann.hu
author_url: http://www.fleischmann.hu/
wordpress_id: 457
wordpress_url: http://fleischmann.hu/wp/?p=457
date: '2010-09-18 12:33:34 +0200'
date_gmt: '2010-09-18 11:33:34 +0200'
categories:
- knowledge
tags:
- knowledge
- MS Windows
- DOS
- script
comments: []
---
<pre><font color="#00FF00" style="font-size:14px">@echo off
cls
rem Timestamp Generator
rem Parse the date (e.g., Fri 02/08/2008)
set cur_yyyy=%date:~10,4%
set cur_mm=%date:~4,2%
set cur_dd=%date:~7,2%
rem Parse the time (e.g., 11:17:13.49)
set cur_hh=%time:~0,2%
if %cur_hh% lss 10 (set cur_hh=0%time:~1,1%)
set cur_nn=%time:~3,2%
set cur_ss=%time:~6,2%
set cur_ms=%time:~9,2%
rem Set the timestamp format
set timestamp=%cur_yyyy%%cur_mm%%cur_dd%-%cur_hh%%cur_nn%%cur_ss%%cur_ms%
rem Do something with it
echo Timestamp: %timestamp%
rem Clear the environment variables
set cur_yyyy=
set cur_mm=
set cur_dd=
set cur_hh=
set cur_nn=
set cur_ss=
set cur_ms=
set timestamp=
</font></pre>
<p>Source: <a href="http://ings.ca/jim/2008/02/10/adding-timestamps-in-a-dos-batch-file/">http://ings.ca/jim/2008/02/10/adding-timestamps-in-a-dos-batch-file/</a></p>
