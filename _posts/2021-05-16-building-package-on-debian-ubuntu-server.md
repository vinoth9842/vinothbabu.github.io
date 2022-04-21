---
layout: post
title: Building Package on Debian/Ubuntu Server
author: Rangsiman Ketkaew
date: "2021-05-16 23:23:00 +0200"
category:
  - Linux
  - Debian
  - Ubuntu
summary: Building Package on Debian/Ubuntu Server
thumbnail: posts/ubuntu.png
permalink: content/22
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Getting Start](#getting-start)
- [Generate KEY id.](#generate-key-id)
- [Send KEY ID to Ubuntu server](#send-key-id-to-ubuntu-server)
- [Generate SSH key](#generate-ssh-key)
- [Setting pbuilder up](#setting-pbuilder-up)
- [Configure your LaunchPad account](#configure-your-launchpad-account)
- [Confirmation for LaunchPad](#confirmation-for-launchpad)
- [Upload SSH key to LaunchPad](#upload-ssh-key-to-launchpad)
- [Configure the shell](#configure-the-shell)
- [Prepare your program](#prepare-your-program)
- [Build .deb file](#build-deb-file)
- [Tips](#tips)

Debian/Ubuntu is one of the most popular Linux distributions. Installing new package or program on Ubuntu is very easy. With apt or apt-get commands, the user can manage their installed package, install new packages, upgrade new versions, removed old packages, etc. However, there are a number of things you need to do to get started building package and developing for Ubuntu community. So I suggest you read this post carefully!

This post will explain how can we build our own Debian/Ubuntu package file and upload it to the server. This means that you can distribute your program to everybody via sudo apt-get install YOUR_PROGRAM command!

## Getting Start

Original document is available at <http://packaging.ubuntu.com/singlehtml/index.html>. Although it is very good reference, but the instruction explained in that document may be too complicated for the end-users. I boil it down and explain it in a way you can follow easily.

## Generate KEY id.

1. Generate KEY id.
```
gpg --full-gen-key
```

2. Follows an interactive question.
- Question 1:
```
Please select what kind of key you want:
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (sign only)
(4) RSA (sign only)
Your selection? 1
```
- Question 2:
```
Please specify how long the key should be valid.
      0 = key does not expire
    n = key expires in n days
    n w = key expires in n weeks
    n m = key expires in n months
    n y = key expires in n years
Key is valid for 0 0
```
- Question 3:
```
Real name: Rangsiman Ketkaew
Email address: rangsiman1993@gmail.com
Comment:
```

3. Check your KEY id
```
gpg --list-secret-keys --keyid-format LONG
```
Output:
```
sec   rsa3072/TESTKEY112233 2019-05-23 [SC] [expires: XXXX-XX-XX]
      4C220144Fd0892C02CF337AC6F0BF90G43CDE61D
uid       [ultimate] Rangsiman Ketkaew <rangsiman1993@gmail.com>
ssb   rsa3072/XXXXXXXXX 2019-05-23 [E] [expires: XXXX-XX-XX]
```

## Send KEY ID to Ubuntu server

```
gpg --send-keys --keyserver keyserver.ubuntu.com TESTKEY112233
```

## Generate SSH key

1. To generate SSH key, use following command:
```
ssh-keygen -t rsa 
```

2. Then you will ask where the ssh key fille will be saved, just enter the default setting.
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/nutt/.ssh/id_rsa): 
```

3. Type and confirm your passphrase.
```
Enter passphrase (empty for no passphrase):
Enter same passphrase again: 
```

4. Done!
```
Your identification has been saved in /home/rangsiman/.ssh/id_rsa.
Your public key has been saved in /home/rangsiman/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:sdfsfsdfsfdsfsdfsfdsfsdfsfsfdsfdsdfsdfsdf rangsiman@Ubuntu
The key's randomart image is:
+---[RSA 2048]----+
|==_.. |
|++ B |
| .O B . |
| _ X = B E |
|+ X B B S . |
| \* = X . . . |
| + = . . |
| + |
| |
+----[SHA256]-----+
```

## Setting pbuilder up

Execute following command

pbuilder-dist <release> create
where <release> is for example xenial, zesty, artful or in the case of Debian maybe sid or buster.

FYI: You can use following command to check Ubuntu code name:
```
lsb_release -a
```
Output:
```
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 18.04.2 LTS
Release: 18.04
Codename: bionic
```

## Configure your LaunchPad account

1. Go to <https://launchpad.net> and create your own account.

2. Confirmation e-mail will be sent to your e-mail.

3. Get back to the terminal. Check your KEY id using:
```
gpg --list-secret-keys --keyid-format LONG
```
Output:
```
sec rsa3072/TESTKEY112233 2019-05-23 [SC] [expires: XXXX-XX-XX]
4C220144Fd0892C02CF337AC6F0BF90G43CDE61D
uid [ultimate] Rangsiman Ketkaew <rangsiman1993@gmail.com>
ssb rsa3072/XXXXXXXXX 2019-05-23 [E] [expires: XXXX-XX-XX] 
```

4. Submit SSH key to Ubuntu server:
```
gpg --send-keys --keyserver keyserver.ubuntu.com TESTKEY112233 
```

5. Go to <https://launchpad.net/~/+editpgpkeys>

6. Append your Key Fingerprint (a long one) to text box, for example,
```
4C220144Fd0892C02CF337AC6F0BF90G43CDE61D 
```

7. Then click "Import Key".

## Confirmation for LaunchPad

Ref: <https://help.launchpad.net/ReadingOpenPgpMail>

1. A confirmation e-mail will be sent to your e-mail.

2. In the e-mail there will be a long PGP KEY message like this:
```sh
---BEGIN PGP MESSAGE---
Version: GnuPG v1
xxxxxxxxxxx
xxxxxxxxxxx
xxxxxxxxxxx
---END PGP MESSAGE---
```

3. Open your terminal and create file call opgpm.txt.
```
vi opgpm.txt 
```

4. Copy and paste the PGP message from the e-mail to the file.

5. Then execute the following command
```sh
gpg -d opgpm.txt 
```

6. Output below confirms that a process is done successfully.
```
gpg: encrypted with 3072-bit RSA key, ID XXXXXXXXXXXX, created 2019-05-23
"Rangsiman Ketkaew rangsiman1993@gmail.com;"
...
...
```

7. Then submit SSH key to Ubuntu server again.
```sh
gpg --keyserver keyserver.ubuntu.com --send-keys TESTKEY112233
```

## Upload SSH key to LaunchPad

1. Go to https://launchpad.net/~/+editsshkeys

2. Copy a key from ~/.ssh/id_rsa.pub and paste to text box and then click Import Public Key.

## Configure the shell

1. Environment variable
```
export DEBFULLNAME="Rangsiman Ketkaew"
export DEBEMAIL="rangsiman1993@gmail.com" 
```

2. Now save the file and either restart your terminal or run:
```
source ~/.bashrc
```

## Prepare your program

1. In this post, I will use a simple program hello world as an example.

2. Download source code of GNU hello version 2.10 from its library.
```
wget -O hello-2.10.tar.gz "http://ftp.gnu.org/gnu/hello/hello-2.10.tar.gz" 
```

2. Uncompress the tarball:
```
tar xf hello-2.10.tar.gz
cd hello-2.10 
```

3. This application uses the autoconf build system so we want to run ./configure to prepare for compilation.
```
./configure 
```

4. Compile program and install it. Binary executable file of hello program will be installed at /usr/local/bin/.
```
make
sudo make install 
```

5. Test program by running:
```
hello
```

## Build .deb file

The following content is proposed by https://ubuntuforums.org/showthread.php?t=910717 .

1. Decide on the name of your package. For example, you could name your first package
```sh
helloworld_2.10-1 
```

2. Create a directory to make your package in. The name should be the same as the package name.
```sh
mkdir helloworld_2.10-1 
```

3. Pretend that the packaging directory is actually the root of the file system. Put the files of your program where they would be installed to on a system.
```sh
mkdir helloworld_2.10-1/usr
mkdir helloworld_2.10-1/usr/local
mkdir helloworld_2.10-1/usr/local/bin
cp "~/Projects/Hello World/helloworld" helloworld_2.10-1/usr/local/bin 
```

4. Now create a special metadata file with which the package manager will install your program...
```
mkdir helloworld_2.10-1/DEBIAN
gedit helloworld_2.10-1/DEBIAN/control 
```

5. Put something like this in that file...
```
Package: helloworld
Version: 2.10-1
Section: base
Priority: optional
Architecture: i386
Depends: debhelper (>= 9)
Maintainer: Rangsiman Ketkaew <rangsiman1993@gmail.com>
Description: Hello World
When you need some sunshine, just run this
small program!
```
(the space before each line in the description is important)

6. Now you just need to make the package:
```
dpkg-deb --build helloworld_1.0-1
```

7. Done!

## Tips

bzr-builddeb includes a plugin to create a new package from a template. The plugin is a wrapper around the dh_makecommand. Run the command providing the package name, version number, and path to the upstream tarball:

```
sudo apt-get install dh-make bzr-builddeb
bzr dh-make hello 2.10 hello-2.10.tar.gz
```

When it asks what type of package type s for single binary. This will import the code into a branch and add the debian/packaging directory. Have a look at the contents. Most of the files it adds are only needed for specialist packages (such as Emacs modules) so you can start by removing the optional example files:

```
cd hello/debian
rm *ex *EX
```
