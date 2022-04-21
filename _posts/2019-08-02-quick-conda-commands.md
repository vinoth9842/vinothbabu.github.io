---
layout: post
title: Quick Conda commands
author: Rangsiman Ketkaew
date: "2019-08-02 19:46:00 +0700"
category:
  - Python
  - cheat-sheet
summary: Important Conda commands you should know
thumbnail: posts/python-conda.png
permalink: content/18
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Conda](#conda)

<br>

## Conda

- Install package, e.g. tensorflow
```
conda install tensorflow
```
- Update conda
```
conda update conda
```
- Update all packages
```
conda update --all
```
- Clean caches, such as tarball files and unused packages.
```
conda clean --all
```
- Create new environment
```
conda create --name NAME_OF_ENV
```
- Activate environment
```
conda activate NAME_OF_ENV
```
- Deactivate environment
```
conda deactivate
```
- Delete unwanted environment
```
conda remove --name NAME_OF_ENV --all
```
