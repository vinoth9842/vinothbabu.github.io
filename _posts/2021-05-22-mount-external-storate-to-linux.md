---
layout: post
title: Mount External Storage to Linux
author: Rangsiman Ketkaew
date: "2021-05-22 10:53:00 +0200"
category:
  - Linux
  - NAS
summary: Mount External Storage to Linux
thumbnail: posts/blog.png
permalink: content/24
comments: true
---

Mount External storage (Flash drive, SSD, HDD, ...) to Linux machine:
Red Hat Enterprise Linux (RHEL)
CentOS
Cloud Linux
Debian
Ubuntu

Type of Mounting

1. NFS recommend for UNIX/Linux OS

2. CIFS recommend for Window OS

- [Check if NAS can be accessed](#check-if-nas-can-be-accessed)
- [Requirements](#requirements)
- [NFS Mount](#nfs-mount)
- [NFS Mount](#nfs-mount-1)
- [Example: Mount NAS to Linux](#example-mount-nas-to-linux)
- [Auto Mount](#auto-mount)


## Check if NAS can be accessed

```
ping 10.100.00.27.141
```

<p align="center">
   <img src="/assets/img/posts/nas-address.png">
</p>

## Requirements

1. Check the Library of NFS and CIFS by searching the file /sbin/mount.<type>  using command 
```
ls /sbin/mount.*
```
If library not found, you can download from server via yum or apt-get command
- For Red-Hat / Fedora
```
sudo yum install nfs.utils
sudo yum install cifs.utils
```
- For Debian/Ubuntu
```
sudo apt-get install nfs-common
```
2. Create Mount Point
Make directory for mount using command like this
```
sudo mkdir /mnt/usb1
```

## NFS Mount

1. Set up directory for mount
```
sudo mkdir /mnt/<insertfoldername> 
```

2. Mount device use NFS type
```
sudo mount -t nfs <IP Address>:/<DriveVolumeName>/<NameofShare> /mnt/<FolderyouCreated> -o user=admin
```

What are them ?
```
-t : type of mounting
nfs : sharing mount
<IP Address>:/ : IP address of external drive
<DriveVolumeName>/ : Name of volume drive
<NameofShare> : Name of drive during sharing
```

## NFS Mount

1. Mount device use CIFS type
```
sudo mount -t cifs <IP Address>:/<DriveVolumeName>/<NameofShare> /mnt/<FolderyouCreated> -o user=admin
```

## Example: Mount NAS to Linux
(read more about NAS)

- NFS
```
sudo mount -t nfs 10.100.27.80:/datavolume/public /mnt/usb -o user=nutt
```
- CIFS
No permission
```
sudo mount -t cifs -o noperm //<IP Address>/<NameofShare> /mnt/<FolderyouCreated>
```
Mount with options: make username & password
```
sudo mount -t cifs //Hostname/Username -o username=username,password=password,rw,nounix,iocharset=utf8,file_mode=0644,dir_mode=0755 /mnt
```
or
```
sudo mount -t cifs //10.100.27.80/Volume_1/ /media/usb/ -o user=nutt
```
or
```
sudo mount -t cifs //10.100.27.80/Volume_1/ /media/usb/ -o credentials=/root/.cifs.txt
```
where .cifs.txt file contains user & passwd, e.g.,
```
username=USER
password=PASSWORD
```

## Auto Mount

Append the following command into the end of /etc/fstab file (root or sudo needed), for example,
```
10.100.27.80:/Volume_1/ /media/usb/  nfs  defaults,nofail  0  0
```
Save and exit. Then mount using command

```
sudo mount /media/usb
 ```

## Unmount

syntax: sudo umount MountPoint. For example,
```
sudo umount  /media/usb/
```
