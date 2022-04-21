---
layout: post
title: Change Static Hostname without Reboot on CentOS
author: Rangsiman Ketkaew
date: "2021-05-22 10:53:00 +0200"
category:
  - Linux
  - Network
summary: Change Static Hostname without Reboot on CentOS
thumbnail: posts/blog.png
permalink: content/23
comments: true
---

Booting the CentOS for first time, the name of Linux machine is set based on the protocal network, which is difficult to remember. When you have many Linux machines, it's better the change the name of each machine. One can do this using a hostnamectl tool.  You can use this command to show the current status of your network and control the system hostname. Learn the definition of each option of hostnamectl using *man hostnamectl* command.

*man* command is always useful for both admin and user.

Step 1: Check the current status of your machine using  hostnamectl status command

The following is an example of output of this command on my Linu machine.

```
   Static hostname: localhost.localdomain
Transient hostname: host-10-100-1-9
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 4633fdd4a93e4e4f944b6fd7455jf8
           Boot ID: 182ff2a5634c42b2a07b497ballr9433
    Virtualization: kvm
  Operating System: CentOS Linux 7 (Core)
       CPE OS Name: cpe:/o:centos:centos:7
            Kernel: Linux 3.10.0-693.17.1.el7.x86_64
      Architecture: x86-64
```

Look at first two lines, the static and transient hostnames of my machine are **localhost.localdomain** and **host-10-100-1-9**.

Step 2: What you have to do is changing the static hostname. You can set new static hostname using *hostnamectl set-hostname new-hostname* command.

```sh
hostnamectl set-hostname RANGSIMAN1993
```

Then, you will be asked to enter the root password. If no any error occurs, you will get message "==== AUTHENTICATION COMPLETE ===".

Step 3: Check the status again using the hostnamectl status

```
   Static hostname: RANGSIMAN1993
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 4633fdd4a93e4e4f944b6fd7455jf8
           Boot ID: 182ff2a5634c42b2a07b497ballr9433
        Machine ID: 4633fdd4a93e4e4f944b6fd7455jf8
           Boot ID: 182ff2a5634c42b2a07b497ballr9433
    Virtualization: kvm
  Operating System: CentOS Linux 7 (Core)
       CPE OS Name: cpe:/o:centos:centos:7
            Kernel: Linux 3.10.0-693.17.1.el7.x86_64
      Architecture: x86-64
```

Now static hostname of your machine is already changed and transient hostname is removed.

When you log-in again, you will see the new hostname.

P.S. If you use hostname command instead of hostnamectl command, it will change you only the transient hostname, not static hostname. This means that hostname of your machine would be back to the old hostname when you reboot a machine.
