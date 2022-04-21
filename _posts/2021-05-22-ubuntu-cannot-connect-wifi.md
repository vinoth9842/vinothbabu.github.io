---
layout: post
title: Ubuntu Cannot Connect WI-FI
author: Rangsiman Ketkaew
date: "2021-05-22 12:43:00 +0200"
category:
  - Linux
  - Ubuntu
  - Wi-Fi
summary: Ubuntu Cannot Connect WI-FI
thumbnail: posts/blog.png
permalink: content/25
comments: true
---

The following is the workaround for fixing Wi-Fi connection of Ubuntu. 

1. Type command:
```
sudo vi /etc/NetworkManager/NetworkManager.conf
```

2. At the bottom of this file, copy and paste the following to a file
```
[device] 
wifi.scan-rand-mac-address=no
```

3. Then restart network of system using command
```
sudo service network-manager restart
```

4. Try to connect Wi-Fi again. 

This solution should also work for other Ubuntu versions.
