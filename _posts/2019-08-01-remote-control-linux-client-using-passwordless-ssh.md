---
layout: post
title: Remote Control Linux Client using Passwordless SSH
author: Rangsiman Ketkaew
date: "2019-08-01 20:28:00 +0700"
category:
  - Linux
  - server
summary: Remote Control Linux Client using Passwordless SSH
thumbnail: posts/cluster-ssh.png
permalink: content/11
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Remote Control Linux Client using Passwordless SSH](#remote-control-linux-client-using-passwordless-ssh)
  - [Step 1. Generating a private key](#step-1-generating-a-private-key)
  - [Step 2. Create automatic script to send token authentication key to all clients](#step-2-create-automatic-script-to-send-token-authentication-key-to-all-clients)
  - [Step 3. Executing script](#step-3-executing-script)

<br>

## Remote Control Linux Client using Passwordless SSH

Suppose that a cluster has mother node and clients nodes whose their hostname are follows:
- compute-1
- compute-2
- compute-3
- compute-4
- compute-5

<br>

### Step 1. Generating a private key

The first step starts with creation of an authentication key on Remote SSH for accessing to client or computing node. 

Run the following command to generate the key.

```
ssh-keygen
```

You will be asked where you want to save the private key files.
Just Enter and the files will be stored in a hidden folder under your home by default setting.

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/rangsiman/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

Enter three times to use default value. Then you will get the warning message. Now it's finished.

```
The key fingerprint is:
--------------------------------------------------- rangsiman@RemoteSSH
The key's randomart image is:
+--[ RSA 2048]----+
| .==. E          |
| o.o.* =         |
|. o = =          |
| + o . +         |
|  + +   S        |
|   o o .         |
|    .            |
|                 |
|                 |
+-----------------+
```

Look at $HOME/.ssh/. There you should have id_ras and id_ras.pub files. Now, copy id_ras.pub to authorized_keys file.

```
cp id_ras.pub authorized_keys
```

<br>

### Step 2. Create automatic script to send token authentication key to all clients

On Remote SSH, create new bash script and copy/paste following code to bash script.

```
cd $HOME/.ssh
for i in compute-{1..5}
  do
  scp -r id_ras id_rsa.pub authorized_keys $USER@$i:$HOME/.ssh/
done
```

<br>

### Step 3. Executing script

Change permission of a bash script using command

```
chmod +x bash_script.sh
```

You also must change the hostname of client before run the script !

Then execute the script

```
./bash_script.sh
```

Files specified in scp line will be sent to compute-1, compute-2, compute-3, compute-4, and compute-5.

When it's done, you are able to access to client using SSH passwordless.
