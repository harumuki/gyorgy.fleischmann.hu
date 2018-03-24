---
layout:   post
title:    ☁️ Apache on Google Cloud Shell
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [unix, development, how to, google, cloud]
---

Hogyan lehet egy teszt apache szervert elindítani a [Goolge Cloud Shell](https://console.cloud.google.com/cloudshell/)-ben? 

<!-- break -->

```shell
sudo apt-get update && sudo apt-get install apache2 -y

echo '<!doctype html><html><body><h1>Hello World!</h1></body></html>' | sudo tee /var/www/html/index.html

sudo vi /etc/apache2/ports.conf

sudo /etc/init.d/apache2 start
```

Tadam!