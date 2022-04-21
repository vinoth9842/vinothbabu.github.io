---
layout: post
title: Installation of RPM package without manually installing dependencies
author: Rangsiman Ketkaew
date: "2021-05-16 23:13:00 +0200"
category:
  - Linux
  - RPM
summary: Installation of RPM package without manually installing dependencies
thumbnail: posts/blog.png
permalink: content/21
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Installation](#installation)
- [Uninstallation](#uninstallation)

Normally Linux user installs the program or package via either yum or rpm tools.  For yum installer, sometimes yum cannot install the package because the repository mirror or yum server database have no those pakcages. Linux experts suggest create of local yum repository, but it is quite not convenient for beginner or novice.  The rpm is an alternative to yum repo method. The rpm file of a certain pakcage can be searched and downloaded from the rpm database.  For example, <https://rpmfind.net>, in this website, user can search desired packages with system and arch optional filter to narrow down the search results.  Then user can download rpm file to Linux machine using wget command and install using rpm installer.

## Installation

The following is rpm command for installation of GTK+-2 package on CentOS 7 64 bit.

```sh
rpm -i gtk2-devel-2.24.31-1.el7.x86_64.rpm
```

Even if RPM normally works well for most of user, but, the problem with this installer is that some package requires user to install the dependecies of package beforehand. I would say that this is one of disadventages of rpm.  However, to deal with this, we can use yum installer to install the package and its dependencies automatically.  So users do not need to install themselve some unknown packages anymore. The followinf command is a solution that I am talking about (refer to the rpm file),

```sh
yum install packagename.arch.rpm
```

or 

```sh
yum --nogpgcheck localinstall packagename.arch.rpm
```

Yum will install a package.arch package automatically.

## Uninstallation

To uninstalled the package, you can use either yum or rpm regardless of installation method.

For the yum team,

```sh
yum remove packagename.arch
```

Note that the name of package does not end in .rpm.

For the rpm team,

First, search the actual full name of package.

```sh
rpm -qa | grep -i "gtk2"
```

Example of output

```sh
adwaita-gtk2-theme-3.22.2-2.el7_5.x86_64
webkitgtk4-plugin-process-gtk2-2.16.6-6.el7.x86_64
ibus-gtk2-1.5.17-2.el7.x86_64
gtk2-immodule-xim-2.24.31-1.el7.x86_64
pygtk2-2.24.0-9.el7.x86_64
oxygen-gtk2-1.3.4-3.el7.x86_64
gtk2-2.24.31-1.el7.x86_64
caribou-gtk2-module-0.4.21-1.el7.x86_64
gtk2-devel-2.24.31-1.el7.i686
gtk2-devel-2.24.31-1.el7.x86_64
pygtk2-libglade-2.24.0-9.el7.x86_64
gtk2-2.24.31-1.el7.i686
```

Then uninstall rm package.

```
rpm -e gtk2-devel-2.24.31-1.el7.i686
```

Finally list rpm package again to confirm that package is already removed.

YSK: The advanced method of user-installed yum repository for expert can be found in the following websites.

1. <https://wiki.centos.org/HowTos/CreateLocalRepos>
2. <https://stackoverflow.com/questions/13876875/how-to-make-rpm-auto-install-dependencies>
