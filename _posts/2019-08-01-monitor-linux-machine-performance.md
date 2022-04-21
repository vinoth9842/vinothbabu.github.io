---
layout: post
title: Monitor Linux Performance using Passwordless SSH
author: Rangsiman Ketkaew
date: "2019-08-01 23:06:00 +0700"
category:
  - Linux
  - server
summary: Monitor Linux Performance using Passwordless SSH
thumbnail: posts/linux-server.png
permalink: content/15
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Monitor Linux Performance using Passwordless SSH](#monitor-linux-performance-using-passwordless-ssh)
- [Automated program for machine performance query](#automated-program-for-machine-performance-query)
- [Getting Program](#getting-program)
- [Read This Before Running The Script](#read-this-before-running-the-script)
- [Example of output](#example-of-output)

<br>

## Monitor Linux Performance using Passwordless SSH

On Linux cluster, multiple compute nodes (SSH client) are connected and environmentally shared under master server (SSH Linux server) as a computer cluster. It is difficult to find out the performance, especially CPUs utilization of all compute nodes at the same time. The most crazy way (but most simple) is accessing to each machine and then use "top" or "free" commands to query the number of CPUs and memory. It can be very big job when you have to deal with a ton of SSH clients, says 20 nodes. In this post I am going to use a simple program for automatically determining computational performance of compute node in HPC cluster. You can use this program on front-end machine, no need to manually access to those compute machines.

<br>

## Automated program for machine performance query

```sh
#!/bin/bash

# How to use:
# 1. Change hostname of SSH client in for loop.
# 2. Password-less SSH is needed.
# 3. Run command "./check-linux-performance.sh".
# 4. This script running slow, be patient !

clear
echo ""
echo -e "\t [] Monitor Performance of SSH Linux Server []\n"
echo "Computing Resource of $(hostname), run by $(whoami)"
#echo "Start on $(date)"
START=$(date +%T)
echo "==============================================================="
printf "%s \t %s \t %s\n" "Hostname" "Free/Total CPUs" "Free/Total Memory (GB)"
echo "==============================================================="
######################### Change The Following Line #############################
for i in compute{1..4}
#################################################################################
do
TOTALCPU=`ssh $i 'grep -c '^processor' /proc/cpuinfo'`
USEDCPU=`ssh $i 'top -bn1|grep "$n" | grep ' R '' | awk '{SUM += $9/100} END {printf "%0.f\n", SUM}'`
FREECPU=$((TOTALCPU-USEDCPU))
TOTALMEM=`ssh $i 'free -m'|awk 'FNR == 2 {printf "%0.2f\n", $2/1024}'`
FREEMEM=`ssh $i 'vmstat -S M'|awk 'FNR == 3 {SUM=($4+$5+$6)/1024} END {printf "%0.2f\n",  SUM}'`
printf "%s \t\t %s \t\t %s\n" "$i" $FREECPU" / "$TOTALCPU $FREEMEM" / "$TOTALMEM
done
echo "==============================================================="
echo "Start on $ST_DATE at $ST_TIME"
echo "Done  on $(date +%D) at $(date +%T)"
```

<br>

## Getting Program

Program code can be downloaded from 
<https://raw.githubusercontent.com/rangsimanketkaew/Linux/master/check-linux-performance.sh>.

1. Download script to your SSH client.
```
wget https://raw.githubusercontent.com/rangsimanketkaew/Linux/master/check-linux-performance.sh
```

2. Change permission
```
chmod +x check-linux-performance.sh
```

3. Execute program
```
. check-linux-performance.sh
```

<br>

## Read This Before Running The Script

1. My script is running slow because of it can access to compute node one at a time.
2. User directories are assumed to be under /home/ directory. If all or some of them is other location, please adjust the code around line number 23.  For example, user directories are different locations: /home1/, /home2/, and /home3. The correct command for searching of user list is following
```
user=($(ls /home1/) $(ls /home2/) $(ls /home3/))
```

3. Do not forget to change host name of compute node.
Most of Linux cluster has SSH clients whose host name are sequence. For example, q1, q2, q3, ... , q99, and q100. You can use regular expression  {  }  for expression of the integer number.
```
for i in q{1..100}
```
Combination of two or multiple variables is supported as well. E.g.,
```
for i in q{1..100} node-0-{1..20} client1 client2 client3
```

<br>

## Example of output

```
         [] Monitor Performance of SSH Linux Server []
Computing Resource of server1, run by nutt
===============================================================
Hostname         Free/Total CPUs         Free/Total Memory (GB)
===============================================================
compute1                 27 / 32                 28.90 / 31.19
compute2                 16 / 32                 24.93 / 31.19
compute3                 16 / 32                 24.37 / 31.19
compute4                 16 / 32                 24.73 / 31.19
===============================================================
Start on 06/03/18 at 02:16:30
Done  on 06/03/18 at 02:16:34
```
