---
layout: post
title: Connect Remote Server using OpenVPN
author: Rangsiman Ketkaew
date: "2019-08-01 16:49:00 +0700"
category:
  - Linux
  - server
summary: Connect Remote Server using OpenVPN with Username/Password Authentication
thumbnail: posts/openvpn.png
permalink: content/10
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [For Windows users](#for-windows-users)
- [For non-Windows users](#for-non-windows-users)
- [Error and Solution](#error-and-solution)

<br>

## For Windows users

1. Download and install OpenVPN from <https://openvpn.net/index.php/open-source/downloads.html> for Window: choose installer _openvpn-install*.exe._
2. Prepare OpenVpn config file (*.ovpn) e.g. openvpn-rangsiman.ovpn.
3. Copy file from (2) to **C:\Program Files\OpenVPN\config\** (or where you installed OpenVPN)  or click at OpenVPN icon at taskbar. Then select _Import file..._ and navigate to openvpn config file.
4. Open OpenVPN by double click its icon on desktop or search on Start Menu --> OpenVPN GUI.
5. Activate OpenVPN by selecting Connect to connect access Linux server.
6. Enter your username and password.
7. Wait until connection completed. Notice that the icon of OpenVPN at taskbar would be changed color from white to orange and to green, respectively.
8. Connection done
9. Caveat: you should disconnect OpenVPN when you have finished SSH.

<br>

## For non-Windows users

1. Open terminal.
2. Install OpenVPN using command  sudo apt-get install openvpn for Ubuntu or Debian-based Linux distribution and sudo yum install openvpn  for Fedora or CentOS Linux distribution.
3. Prepare your config file (*.ovpn) e.g. _openvpn-rangsiman.ovpn_ and save it at your home directory: 
```
/home/rangsiman/vpn/
```
4. Create passwd authentication file e.g. passwd.txt. Then put your username and passwd to this file.
5. Connect VPN using command
```
sudo openvpn --config /home/rangsiman/vpn/openvpn-rangsiman.ovpn --auth-user-pass /home/rangsiman/vpn/passwd.txt --auth-nocache
```
6. Enter your sudo password.
7. Wait until you see status message "Initialization Sequence Completed".
8. Now you are ready to connect access Linux server.

_You can watch this video for step-by-step using OpenVPN on Linux._

<br>

## Error and Solution

If you face an error like this

```
Fri May 25 13:54:07 2018 failed to find GID for group nogroup
Fri May 25 13:54:07 2018 Exiting due to fatal error
```

This can be solve by change the group name in OpenVPN configuration file. For example,  

```
user nobody
group nogroup
```

change to

```
user nobody
group nobody
```
