---
layout: post
title:  "GSoC 2020 Nmstate project update for June"
date:   2020-07-01 18:20:01 +0530
categories: Fedora GSoC Nmstate 
---
### [Click to read Fedora Community Blog post][blog_link]

This blog is about my experience working in [Nmstate][nmstate_pg] project and first month in GSoC coding period. I was able to start working on implementing the varlink support mid of community bonding period. This was very helpful because I was able to identify some issues in the python varlink package that was not mentioned in documentation and I had to spend more time finding the cause of the issue. There have been minor changes to proposed code structure and project timeline after the feedback from the community members. In the beginning it was difficult to identify syntax errors in varlink interface definitions. This has been slow progress because of new issues and following are the tasks I have completed so far.

* Defining varlink interface file
* Implementing varlink support of libnmstate functions.
* Defined test cases for varlink functions using the varlink client.
* Created the documentations for varlink support for libnmstate.
* Integrating with the package.

During this coding period I learned about containers and containerized testing. I have been learning about rpm packaging and python package formats recently to understand failing dependency. My mentors’ feedback and support was very helpful in identifying and understanding the issues. Looking forward for new challenges and learning more next in next phase of coding period.


[nmstate_pg]: https://www.nmstate.io/ 
[blog_link]: https://communityblog.fedoraproject.org/gsoc-2020-nmstate-project-update-for-june/