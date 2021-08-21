---
layout: post
title:  "GSoC 2021 Ceph Project Work Product"
date:   2021-08-21 12:00:01 +0530
categories: Ceph GSoC Summer-Coding BDD behave
---
# Implementing new integration testing for Ceph orchestrator using behavior-driven development technique
 
## Mentee
Arunagirinadan Sudharshan
* Github handle : [`@SudhanAruna`](https://github.com/SudhanAruna)
 
## Mentors
 
* Juan Miguel Olmo  : [`@jmolmo`](https://github.com/jmolmo)
 
## About the project and tasks
The project aim is to implement new integration testing for the ceph orchestrator layer using BDD (behavior-driven development) framework. To implement the feature I used, [Behave](https://behave.readthedocs.io/en/stable/philosophy.html) python framework and [Kcli](https://kcli.readthedocs.io/en/latest/) tool. Using Behave the test scenarios are written in Gherkin languages and tested using the python implementations. Using kcli tool we will be able to create, manage and interaction with the virtual machines which are required to testing the scenarios. 

## Progress
I started referring to additional documentations on behave framework and ceph to improve my understanding. Also discussed about the project implementation with my mentor and the ceph orchestrator team during the community bonding period.  
 
Following are links for pull requests created using coding period.
 
* __Implemented basic test scenarios for cephadm, ceph shell and OSD commands__ [PR #419181](https://github.com/ceph/ceph/pull/41918)
 
    As the main objectives, I implemented the following functionalities which are included in the above pull request.
 
    * Parsing description provided to create and manage the environments using kcli for executing the test cases.
    * Functions to execute the test case commands and validating the output.
    * Created different test scenarios for cephadm commands, ceph shell commands and OSD creations. 
 
 
Currently in work in progress
 * __Implementing RDB commands test cases__ [PR #42877](https://github.com/ceph/ceph/pull/42877)
    
    In this pull request I have included new test case which require additional funcationality for executing the command so I'm continuing to improve the code to support them.


## To do
 
I'll be continuing to add different test scenarios of ceph orchestrator and if requried modify the code to support them.
 
