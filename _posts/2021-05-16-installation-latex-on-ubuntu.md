---
layout: post
title: Installation of LaTeX on Ubuntu
author: Rangsiman Ketkaew
date: "2021-05-16 17:11:00 +0200"
category:
  - LaTeX
  - Linux
summary: Installation of LaTeX on Ubuntu
thumbnail: posts/blog.png
permalink: content/20
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Installation of TeX Live on Ubuntu 16.04.](#installation-of-tex-live-on-ubuntu-1604)

<br>

## Installation of TeX Live on Ubuntu 16.04.

1. Open linux terminal

2. Download package via repository ppa "jonathonf"
```sh
sudo add-apt-repository ppa:jonathonf/texlive
```

3. Update package
```sh
sudo apt-get update
```

4. Install texlive first
```sh
sudo apt-get install texlive-full
```

5. Install texstudio
```sh
sudo apt-get install texstudio
```

## Uninstall texlive using purge command

```sh
sudo apt install ppa-purge && sudo ppa-purge ppa:jonathonf/texlive
```

## Installation & uninstall of TexStudio

```sh
sudo apt-get install texstudio
sudo apt-get purge texstudio\*
```

