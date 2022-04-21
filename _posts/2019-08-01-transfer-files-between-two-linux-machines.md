---
layout: post
title: File transfer between two Linux machines
author: Rangsiman Ketkaew
date: "2019-08-01 20:37:00 +0700"
category:
  - Linux
  - server
summary: File transfer between server and local host machines
thumbnail: posts/file-transfer.png
permalink: content/12
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [File transfer between two Linux machines](#file-transfer-between-two-linux-machines)
- [Help page of scp](#help-page-of-scp)
- [Transfers single file/folder](#transfers-single-filefolder)
- [Transfers multiple files/folders](#transfers-multiple-filesfolders)
- [Optional commands](#optional-commands)
- [Caveat](#caveat)

<br>

## File transfer between two Linux machines

Transfers file or folder between two Linux machines, for example, sending file from a remote server (master node) to compute node and vice versa, can be done easily with a scp command.

A _scp_ or _secure copy_ allows secure transferring of files between two machines encrypting using SSH private key. It uses the same authentication and security algorithm as a secure shell (SSH) protocol from which it is based. The scp is able to transfer you both single or multiple files and folders simultaneously. Moreover, It is simplicity, secure, and fast.

<br>

## Help page of scp

You can use _man_ command to open a manual of scp, like this:

```
man scp
```

which will show the output like this

```
SCP(1)                                                   BSD General Commands Manual                                                  SCP(1)

NAME
     scp — secure copy (remote file copy program)

SYNOPSIS
     scp [-346BCpqrTv] [-c cipher] [-F ssh_config] [-i identity_file] [-l limit] [-o ssh_option] [-P port] [-S program] [[user@]host1:]file1
         ... [[user@]host2:]file2

DESCRIPTION
     scp copies files between hosts on a network.  It uses ssh(1) for data transfer, and uses the same authentication and provides the same
     security as ssh(1).  scp will ask for passwords or passphrases if they are needed for authentication.

     File names may contain a user and host specification to indicate that the file is to be copied to/from that host.  Local file names can
     be made explicit using absolute or relative pathnames to avoid scp treating file names containing ‘:’ as host specifiers.  Copies
     between two remote hosts are also permitted.

etc ...
```

<br>

## Transfers single file/folder

Here is the normal syntax for single file transfer.

1. From a local machine to a remote machine:
```
scp  file  user@ip-address:/remote/directory/
```

2. From a remote machine to a local machine:
```
scp user@ip-address:/remote/directory/file  /local/directory/
```

<br>

## Transfers multiple files/folders

For sending multiple files, one can use regular expression  "{" and "}" for grouping all files and send them all at the same time.

1. From a local machine to a remote machine:
```
scp  file1 file2 file3 ...  user@ip-address:/remote/directory/
```
or
```
scp  file.*  user@ip-address:/remote/directory/
```
or
```
scp  file{1,2,3}  user@ip-address:/remote/directory/
```

2. From a remote machine to a local machine:
```
scp user@ip-address:/remote/directory/\{file1,file2,file3\}  /local/directory/
```

<br>

## Optional commands

You can also specify port number of remote machine, like this:

```
scp  -P  <port_number_of_remote>  file1 file2 ... user@ip-address:/remote/directory
```

<br>

## Caveat

For scp, you can specify port number using only "-P" (big P).
