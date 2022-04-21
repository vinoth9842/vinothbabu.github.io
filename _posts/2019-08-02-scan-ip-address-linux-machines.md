---
layout: post
title: Scan IP address of Linux machines
author: Rangsiman Ketkaew
date: "2019-08-02 16:06:00 +0700"
category:
  - Linux
  - server
summary: Scan IP address of Linux machines using command line
thumbnail: posts/ip-address.png
permalink: content/16
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Scan IP address using command line](#scan-ip-address-using-command-line)

<br>

## Scan IP address using command line

Nmap is a free and open-source security scanner, originally written by Gordon Lyon, used to discover hosts and services on a computer network, thus building a "map" of the network. Obviously, Nmap or nmap can be used to scan IP address of your HPC cluster network.

1. Install nmap package
The following commands to install nmap on RHEL-based and Ubuntu, respectively.
```
sudo yum install nmap
sudo apt-get install nmap
```

2. Check version
```
nmap --version
```

3. Scan IP address
- For nmap version 6.x or higher   
```
nmap -sn 192.168.1.1/4       
```
This will scan from 192.168.1.1 to 192.168.1.4
- For nmap version 5.x or lower    
```
nmap -sP 192.168.1.1/4
```
This will scan from 192.168.1.1 to 192.168.1.4

More details of nmap can be found on its official website: [htpps://www.nmap.org](htpps://www.nmap.org)
