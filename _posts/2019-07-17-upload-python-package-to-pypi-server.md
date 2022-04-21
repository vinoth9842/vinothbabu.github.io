---
layout: post
title: Upload Python package to PyPI library
author: Rangsiman Ketkaew
date: "2019-07-17 17:07:00 +0700"
category:
  - Python
  - how-to
summary: Upload Python package to PyPI library
thumbnail: posts/python-logo.png
permalink: content/3
redirect_from: /python/how-to/2019/07/17/upload-python-package-to-pypi-server
comments: true
---

# Upload Python package to PyPI library

---

- [Upload Python package to PyPI library](#upload-python-package-to-pypi-library)
  - [Python Package Index (PyPI)](#python-package-index-pypi)
  - [Prerequisite packages](#prerequisite-packages)
  - [First of all, you should have](#first-of-all-you-should-have)
  - [Creating configuration file](#creating-configuration-file)
  - [Building distribution files](#building-distribution-files)
  - [Upload package to server](#upload-package-to-server)
    - [Test-PyPI](#test-pypi)
    - [PyPI](#pypi)
  - [Searching Package](#searching-package)
    - [Test-PyPI](#test-pypi-1)
    - [PyPI](#pypi-1)
    - [Show package detail](#show-package-detail)
  - [Installing](#installing)
    - [Test-PyPI](#test-pypi-2)
    - [PyPI](#pypi-2)
  - [Reference:](#reference)

## Python Package Index (PyPI)

This post covers the basic of how to build and distribution your own Python package and upload it to Python package index (PyPI) library in order to the other develops of the end-users can install and use it easily. It is not difficult and everyone can do it! Follow the below instruction step-by-step, when it is done, you and other people can type just pip install your_project to install your package!

## Prerequisite packages

- Python 3.x

```sh
python --version
```

- setuptools
- wheel
- twine

```sh
pip install setuptools wheel twine --upgrade --user
```

## First of all, you should have

- Project source code
- Github repository (optional, but highly recommended)
  - LICENSE
  - README.md
- Test-PyPI account (optional, but highly recommended)
- PyPI account

## Creating configuration file

setup.py

```py
#!/usr/bin/env python

import setuptools

**version** = "x.x.x" # version of your package

with open("README.md", "r", encoding="utf-8") as f:
long_description = f.read()

description = "This is my project" # description of package

setuptools.setup(
name="YOUR_PACKAGE_NAME", # your package name
version=**version**,
author="PACKAGE_NAME", # author name
author_email="AUTHOR_EMAIL", # author e-mail
description=description,
long_description=long_description,
long_description_content_type="text/markdown",
url="LINK_TO_WEBSITE", # link to project website
download_url="RELEASE_FILE", # link to release archive
project_urls={
'Documentation': 'PROJECT_DOCS', # link to package document
'Source': 'PROJECT_SOURCE_CODE', # link to project source code
},
packages=setuptools.find_packages(),
install_requires=[
'numpy' # list of package dependencies, fx, numpy
],
classifiers=[
"Programming Language :: Python",
"Programming Language :: Python :: 3",
"Development Status :: 5 - Production/Stable",
"License :: OSI Approved :: GNU General Public License v3 (GPLv3)",
"Operating System :: OS Independent",
"Intended Audience :: Developers",
"Natural Language :: English",
],
python_requires='>=3',
)
```

## Building distribution files

Build *.tar.gz source code archive and *whl distribution files using command:

```sh
python setup.py sdist bdist_wheel
```

Both *tar.gz and *whl will be built and stored in a ./dist directory.

## Upload package to server

### Test-PyPI

Upload file

```sh
twine upload --repository-url https://test.pypi.org/legacy/ dist/\*
```

It will ask you to enter your PyPI account, for example:

```sh
Enter your username: rangsiman
Enter your password: (invisible)
Uploading distributions to https://test.pypi.org/legacy/
Uploading octadist-2.5.3-py3-none-any.whl
100%|████████████████████████████████████| 51.3k/51.3k [00:03<00:00, 14.5kB/s]
Uploading octadist-2.5.3.tar.gz
100%|████████████████████████████████████| 33.4k/33.4k [00:01<00:00, 20.7kB/s]
```

### PyPI

Upload file

```sh
twine upload dist/\*
```

It will ask you to enter your PyPI account, for example:

```sh
Enter your username: rangsiman
Enter your password: (invisible)
Uploading distributions to https://upload.pypi.org/legacy/
Uploading octadist-2.5.3-py3-none-any.whl
100%|████████████████████████████████████| 51.3k/51.3k [00:03<00:00, 14.5kB/s]
Uploading octadist-2.5.3.tar.gz
100%|████████████████████████████████████| 33.4k/33.4k [00:01<00:00, 20.7kB/s]
```

## Searching Package

### Test-PyPI

```sh
pip search octadist --index https://test.pypi.org/pypi
```

### PyPI

```sh
pip search octadist --index https://pypi.org/pypi
```

or

```sh
pip search octadist
```

### Show package detail

```sh
pip show octadist
```

Sample output:

```sh
Name: octadist
Version: 2.5.3.1
Summary: OctaDist: A tool for calculating distortion parameters in coordination complexes.
Home-page: https://octadist.github.io
Author: Rangsiman Ketkaew
Author-email: rangsiman1993@gmail.com
License: UNKNOWN
Location: c:\xxx\xxx\xxx\anaconda3\lib\site-packages
Requires: matplotlib, rmsd, numpy, scipy
Required-by:
```

## Installing

### Test-PyPI

```sh
pip install --index-url https://test.pypi.org/simple/ octadist
```

### PyPI

```sh
pip install octadist
```

## Reference:

1. Overview: https://packaging.python.org/overview/
2. Tutorial: https://packaging.python.org/tutorials/
3. Packaging and distributing tools: https://packaging.python.org/guides/distributing-packages-using-setuptools/
