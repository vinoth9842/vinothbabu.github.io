---
layout: post
title: Install Linux libraries
author: Rangsiman Ketkaew
date: "2021-05-26 15:42:00 +0200"
category:
  - Linux
  - libraries
summary: Install Linux libraries
thumbnail: posts/blog.png
permalink: content/26
comments: true
---

- [wget](#wget)
- [nettle](#nettle)
- [gnutls](#gnutls)

## wget

```sh
./configure \
  --without-libgnutls-prefix \
  --with-ssl=openssl \
  --prefix=/users/rketkaew/src/wget-1.21.1-installed
make
make install
```

## nettle

```sh
./configure \
  --prefix=/users/rketkaew/src/nettle-3.6-installed \
  --enable-mini-gmp
make
make install
```

## gnutls

```sh
./configure \
  --prefix=/users/rketkaew/src/gnutls-3.7.1-installed/ \
  NETTLE_LIBS="-L/users/rketkaew/src/nettle-3.6-installed/lib64/" \
  NETTLE_CFLAGS="-I/users/rketkaew/src/nettle-3.6-installed/include/nettle/" \
  HOGWEED_LIBS="-L/users/rketkaew/src/nettle-3.6-installed/lib64/" \
  HOGWEED_CFLAGS="-I/users/rketkaew/src/nettle-3.6-installed/include/nettle/" \
  GMP_LIBS="-L/users/rketkaew/src/gmp-6.2.1-installed/lib/" \
  LIBTASN1_LIBS="-L/users/rketkaew/src/libtasn1-4.17.0-installed/lib/" \
  LIBTASN1_CFLAGS="-I/users/rketkaew/src/libtasn1-4.17.0-installed/include/" \
  --with-included-unistring
make
make install
```
