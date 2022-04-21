---
layout: post
title: Segmentation fault in your program
author: Rangsiman Ketkaew
date: "2019-08-02 18:29:00 +0700"
category:
  - Linux
  - server
  - parallelization
  - MPI
  - OpenMP
summary: What is segmentation fault and how to handle it
thumbnail: posts/segfault.png
permalink: content/17
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Segmentation Fault](#segmentation-fault)
- [Debugging](#debugging)

<br>

## Segmentation Fault

It is possible to run the calculation on high performance computer (HPC) using a tons of CPU cores, says 1200 cores. For a large number of CPU cores, Message Passing Interface (MPI) can help you for running your program in parallel over multiple CPU processors and/or multiple compute nodes. Nowadays, there is many MPI candidates which is powerful, user-friendly, and free, such as OpenMPI, Intel MPI, MPICH, and MVAPICH. Calculation can be done successfully, without any error. However, most of people frequently confront the error when using pure MPI or Hybrid (MPI+OpenMP) for running the program or application in parallel.

The following is a standard error message you have ever found before or may be similar with:

```
===================================================================================
=   BAD TERMINATION OF ONE OF YOUR APPLICATION PROCESSES
=   PID 182825 RUNNING AT COMPUTE-100
=   EXIT CODE: 6
=   CLEANING UP REMAINING PROCESSES
=   YOU CAN IGNORE THE BELOW CLEANUP MESSAGES
===================================================================================
===================================================================================
=   BAD TERMINATION OF ONE OF YOUR APPLICATION PROCESSES
=   PID 182825 RUNNING AT COMPUTE-100
=   EXIT CODE: 6
=   CLEANING UP REMAINING PROCESSES
=   YOU CAN IGNORE THE BELOW CLEANUP MESSAGES
===================================================================================
   Intel(R) MPI Library troubleshooting guide:
      https://software.intel.com/node/561764
===================================================================================
```

This error is called **segmentation fault** or **segfault**. Typically, the segmentation fault is error in the program or application that you use, not in MPI. Therefore, before running any parallel calculation using MPI, you should carefully check that your program/application is designed for this task of calculation. 

<br>

## Debugging

To overcome the segmentation fault, you can use the debugger such as _gdb_, _ddd_, _totalview_, and _padb_ for debugging segmentation fault in your program. In Linux, you can try first with "gdb" or "ddd". But, these tools are serial debuggers. If you want to use parallel debugger, please use "totalview" as describes below.

- For gdb, you can use command like this: 
```
mpiexec -np 4 xterm -e gdb ./your_program
```

- For ddd, you can use
mpiexec -np 4 ddd ./foo/your_program

- Moreover, the "totalview" debugger allows multiple levels of debugging for MPI programs. If you need to debug your application without any information from the MPICH stack, you just need to compile your program, like this:
```
mpicc -g
```
and then run your application using command:
```
totalview mpiexec -a -f machinefile ./your_program
```
