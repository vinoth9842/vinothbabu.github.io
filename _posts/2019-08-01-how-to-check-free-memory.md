---
layout: post
title: How to check free memory
author: Rangsiman Ketkaew
date: "2019-08-01 21:41:00 +0700"
category:
  - Linux
  - server
  - how-to
summary: Check memory usage of your individual Linux machine and cluster
thumbnail: posts/memory-ram.png
permalink: content/14
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Check Free Memory on Linux](#check-free-memory-on-linux)
- [Let's go](#lets-go)
- [Make it automatic for checking all machines](#make-it-automatic-for-checking-all-machines)

<br>

## Check Free Memory on Linux

To determine the memory usage of Linux machine for running program, I believe that you can google for this. But, several results may confuse you that which one is the most efficient tool/way for this. After my hard finding, I found that a **free** command is the best choice that fits best for checking memory usage, at least for me LOL. The free command can quantify and display the total amount of free and used physical memories, swap memory in the system, and the buffers memory that used by the kernel.

To do so, just type like this:

```
free -g
```

This will show you the total, used, and free memories in human-readable units.

<br>

## Let's go

I suggest you use free command with -g is optional so that the amount of memory will be shown in Gigabytes which is understandable for anyone.

```
             total       used       free     shared    buffers     cached
Mem:            62         54          8          1          2         45
-/+ buffers/cache:          6         56
Swap:           99          4         95
```

* Total memory is  62 GB
* Used memory is  6 GB   (2nd row)
* Free memory is  56 GB   (2nd row)

or

```
              total        used        free      shared  buff/cache   available
Mem:             31           0          23           0           6          29
Swap:            15           0          15
```

* Total memory is  31 GB
* Free memory is  29 GB  (+ buffers/cache)

<br>

## Make it automatic for checking all machines

To automatically determine the memory usage of multiple remote machines at the same time, you may use the following code shell script. I wrote this script for my system. If it fails on your system, you may have to tweak the code a little bit.

```
#!/bin/bash

for i in compute-1 compute-2 compute-3 compute-4 compute-5 compute-6
do
CPU=`ssh $i "grep -c '^processor' /proc/cpuinfo"`
MEM1=`ssh $i "free -g|grep 'buffers/cache'"`
MEM2=`ssh $i "free -g|grep 'Mem'"`
echo "$i $MEM1" > mem.info.$i
echo "$i $MEM2" >> mem.info.$i
#MEMCHECK=`grep 'buffers' mem.info.$i`
if [ $(grep -c "buffers" mem.info.$i) -ne 0 ];then
FREEMEM=`awk 'FNR == 1 {print $5}' mem.info.$i`
else
FREEMEM=`awk 'FNR == 2 {print $8}' mem.info.$i`
fi
echo "Node: $i : Number of Processor = $CPU cores and Free Memory = $FREEMEM GB"
rm mem.info.$i
done
```

P.S. You need a passwordless SSH for accessing all machines that you list in for loop.
