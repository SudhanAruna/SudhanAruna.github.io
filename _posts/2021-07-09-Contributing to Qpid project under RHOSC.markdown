---
layout: post
title:  "Contributing to Qpid project under RHOSC"
date:   2021-07-09 12:20:00 +0530
categories: RHOSC Qpid Proton CFFI
---

# Contributing to Qpid project under RHOSC
During the April of 2021, I got selected to participate in the Redhat Open Source Contest 2021 to contribute to the Qpid project under.


### __Mentor__ Jiri Danek (Github handle : ```@jiridanek```)


* [Upstream project PR draft](https://github.com/apache/qpid-proton/pull/318)

* [Commits](https://github.com/apache/qpid-proton/pull/318/commits)

__Work in Progress PRs__

Following are the PRs still in progress 
* [Fixing Transport test cases PR](https://github.com/jiridanek/qpid-proton/pull/32)    
* [Fixing Reactor test cases PR](https://github.com/jiridanek/qpid-proton/pull/33)

## About the contest and project
I came across RHOSC (Redhat open source contest) while looking for some research project to contribute. This contest encourages student to participate in open source projects. [Qpid proton](https://qpid.apache.org/proton/index.html) is a high-performance and lightweight messaging library.

The project is focused on porting python binding from using [Swig](http://www.swig.org/exec.html) to [CFFI](https://cffi.readthedocs.io/en/latest/overview.html) in Qpid proton. CFFI enables us to call C code from python without an interface or intermediate domain language. I was new to the C binding with python project so I had to learn about both Swig and CFFI.  


## Progress

After discussing about the project and tasks initially with my mentor. I referred to the documentations of CFFI to improve understanding the implementation. As the first task, we had to modify the CI for compiling the c functions (using API out-of-line mode) to a shared object file and run only the python test cases. During this period I improved my knowledge on cmake tools and identified an issue in CI with the help of my mentor and opened my first [ticket](https://issues.apache.org/jira/browse/PROTON-2391) in the project. 

To compile the C functions it should be included in the FFI.cdef function but we can’t directly read the C header files because it can not contain some directives like `#ifdef` and `#include`. First I had to write a separate python script file to read C header files and extract only __functions, constants and global variables__ and some types had to be manually included. 

After successfully compiling the message and data C header files in CFFI, I started amending the proton python files to return correct objects because the compiled C functions return cdata type and function require cdata type as arguments. After a few days of struggle and with feedback for my mentor I was able to pass the failing test cases of message and data. We were able to get the feedback on our approach in mid June from the up-stream project. According to the feedback we had to change the approach and continue to fixing the other failing test cases.

Even though I was able to compile most of the C header files, I was unable to fix the other failing test cases because some function returned NULL value and we couldn’t identify the issue. During the two months period, I was able to progress with the support from my mentor. 

I'll continue working on this issue and I’m looking forward to contributing to other issues in the future.
 
