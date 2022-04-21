---
layout: post
title: Installing Intel Parallel Studio XE
author: Rangsiman Ketkaew
date: "2019-07-31 21:38:00 +0700"
category:
  - Math-library
  - software-development
  - installation
  - Intel
  - Linux
summary: How to compile and install Intel Parallel Studio XE 2018 Edition 3
thumbnail: posts/intel-parallel-studio.png
permalink: content/9
comments: true
---

## Table of Content

- [Table of Content](#table-of-content)
- [Intel® Parallel Studio XE](#intel-parallel-studio-xe)
- [Intel® Parallel Studio XE Now Free for Student and Educator](#intel-parallel-studio-xe-now-free-for-student-and-educator)
- [Software Download](#software-download)
- [Prerequisites](#prerequisites)
- [Installation Instruction](#installation-instruction)
- [Setting Up the Build Environment for MPI and MKL, and C++ & Fortran compiler](#setting-up-the-build-environment-for-mpi-and-mkl-and-c--fortran-compiler)
- [Path environment variable setting.](#path-environment-variable-setting)
- [Reference](#reference)

<br>

## Intel® Parallel Studio XE

Intel® Parallel Studio XE is a software development product developed by Intel that facilitates native code development on Windows, macOS and Linux in C++/C and Fortran for parallel computing. This software suite also includes a message passing interface (MPI) and a math kernel library (MKL) entirely developed by Intel.

Several benchmark testing the performance of C++ and Fortran compilers have shown that Intel compiler is very powerful. For example, this article  shows the comparison of C++ compilers in compilation speed and performance of compiled code. In summary, Intel is at least 1.5 time relative to G++ compiler.

<br>

## Intel® Parallel Studio XE Now Free for Student and Educator

Intel has been providing Intel® Parallel Studio XE (IPSX) suite. The latest stable version of Intel Parallel Studio XE that released on the day I write this post is Intel® Parallel Studio XE 2018 update 3. Price for commercial or company license of this version is about 11,000 - 25,000 \$. However, for education, student (at least 18 years old) and educator can get this suite in free of charges.

Intel just released out the 2019 BETA update 1 of IPSX. You can try this version and help Intel to improve their software by sending the feedback or comments after your evaluation. The link to a home page of this suite is <https://software.intel.com/en-us/articles/intel-parallel-studio-xe-2019-beta>. Please note that the beta program officially ends July 19, 2018 and beta licenses expire October 11, 2018.

<br>

## Software Download

The followings are step-by-step registration of Intel account.

1. Firstly, you have to register Intel account with your institute e-mail, e.g., _rangsiman_k@sci.tu.ac.th_. Also note that the company e-mail domain like _@gmail.com_ and _@hotmail.com_ are not allowed. Student may probably contact the staff of library at a campus.

2. Login to Intel product portal using a verified account. You can browse and choose which the software suites you want to download, then Intel will send you an e-mail with a serial number.

3. Follow instruction provided in the e-mail Intel sent you way for downloading program installer as well as a serial number and validate date.

4. For more details, visit this fantastic website: <https://software.intel.com/en-us/qualify-for-free-software/student>

5. Copy a download link and use wget command to download a program source code to your Linux, for example,
```
wget /link/to/location/of/parallel_studio_xe_2018_update3_cluster_edition.tgz
```

<br>

## Prerequisites

1. Operating System
* Debian 8, 9
* Fedora 25, 26
* Red Hat Enterprise Linux 6, 7 (the equivalent CentOS* versions are supported, but not separately tested)
* SUSE Linux Enterprise Server 11, 12
* Ubuntu 14.04, 16.04, 17.04

2. RAM memory: 2 GB

3. Free disk space: 16
* 4 GB for a compressed source code
* 12 GB for installed Intel Parallel Studio XE) GB

4. Bash or C-shell interpreter

5. Serial number (get from e-mail that Intel sent you)

<br>

## Installation Instruction

The following is an installation instruction of Intel® Parallel Studio XE 2018 Update 3. For this writing, I tested the installation of the software suite with my student license on RHEL 7 cluster. This software suite can also be installed on RHEL-based distribution such as CentOS.

1. Uncompress the tgz tarball
```
tar -xzvf parallel_studio_xe_2018_update3_cluster_edition.tgz
```

2. Navigate to IPSX directory and execute _install.sh_ script
```
cd parallel_studio_xe_2018_update3_cluster_edition
./install.sh
```

3. Select Run as current user (Select _1_ if you are root or _2_ if you are sudo)
```
3 & enter
```

4. Select 6 to proceed installation
```
6 & enter
```

5. Read agreement document and information. Then type accept to proceed installation
```
accept & enter
```

6. Type _1_ if you want to consent your information, if not type 2
```
2 & enter
```

7. Installer will be checking the prerequisites. Wait for a while.

8. Select _1_ to activate IPSX using a serial number
```
1 & enter
```

9. Type your serial number and enter to proceed.
```
YOUR-SERIALNUMBER
```

10. Wait a second until serial number checking is finished.

11. Enter to finish configuration installation
```
1 & enter
```

12. Pre-install package summary appears, type _q_ to quit.

13. Enter to start installation and wait for 5 - 10 minutes.
<p align="center">
<img 
  src="/assets/img/posts/intel-parallel-studio-install.png" 
  alt="intel-parallel-studio-install" 
  width="60%" 
  height="auto"
/>
</p>

14. If installation is finished, the dialog appears with following messages.
```
Thank you for installing Intel(R) Parallel Studio XE 2018 Update 3
Cluster Edition for Linux\*.
```

15. The following is a screenshot of the structure of Intal Parallel Studio XE 2018 edition 3 elucidated by _tree_ command.
<img 
  src="/assets/img/posts/intel-parallel-studio-structure.png" 
  alt="intel-parallel-studio-structure" 
  width="100%"
  height="auto" 
/>

<br>

## Setting Up the Build Environment for MPI and MKL, and C++ & Fortran compiler

1. General Parallel Studio XE environment set up
Suppose that \$INTEL_ROOT is set to Intel PSX top directory.
```
source \$INTEL_ROOT/parallel_studio_xe_2018/psxevars.sh
```

2. MPI environment set up
Refers to mpivars.sh shell script in the MPI top directory ($MPI_ROOT), the script is located in $MPI_ROOT/intel64/bin/
```
source \$MPI_ROOT/intel64/bin/mpivars.sh
```

3. MKL environment set up
Refers to mklvars.sh shell script in the MKL top directory ($MKL_ROOT), the script is located in $MKL_ROOT/intel64/bin/
The following command for intel64 and 8 byte integers, use lp64 instead for 4 bytes integer.
```
source \$MKL_ROOT/bin/mklvars.sh intel64 ilp64
Use mkl_help for help
```

4. ++ & Fortran compiler environment set up
Refers to compilervars.sh shell script in the top directory of IPSX, the script is located in \$INTEL_ROOT/bin/
```
source \$INTEL_ROOT/bin/compilervars.sh -arch intel64 -platform linux
```

\*\* The following commands are advisable when calling MPI in order to unlock amount of memory.
```
ulimit -l unlimited
```
To check if memory is set to unlimited, just type following command without any optional setting.
```
ulimit -l
```
The output of this command should say unlimited.

<br>

## Path environment variable setting.

1. Append the following command lines to your \$HOME/.bashrc file.
```
export INTEL_LINUX=$HOME/intel/parallel_studio_xe_2018/compilers_and_libraries_2018/linuxexport 
export PATH=$INTEL_LINUX/bin/intel64/:$INTEL_LINUX/mpi/intel64/bin:$PATH
export I_MPI_ROOT="$HOME/intel/parallel_studio_xe_2018/compilers_and_libraries_2018/linux/mpi"
export MPI_ROOT="$I_MPI_ROOT/intel64"
```

2. Activate .bashrc using command
```
source \$HOME/.bashrc
```

<br>

## Reference

1. <https://software.intel.com/en-us/download/parallel-studio-xe-2018-install-guide-linux>
2. <https://software.intel.com/en-us/get-started-with-mpi-for-linux>
3. <https://software.intel.com/en-us/articles/setting-up-the-build-environment-for-using-intel-c-or-fortran-compilers>
