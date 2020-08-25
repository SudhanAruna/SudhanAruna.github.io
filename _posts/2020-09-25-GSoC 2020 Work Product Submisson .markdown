---
layout: post
title:  "GSoC 2020 Work product"
date:   2020-08-25 12:20:01 +0530
categories: Fedora GSoC Nmstate Summer-Coding
---
# Adding varlink support for Nmstate: GSoC 2020 under Fedora projects

## Mentee
Arunagirinadan Sudharshan
* Github handle : ```@SudhanAruna```

## Mentors

* Fernando Fernandez Mancera
* Till Maas
* Gris Ge

## About the project and tasks
Nmstate is a python library that manages the networking setting of the host using the NetworkManger to apply the configuration. Tasks assigned to me as a GSoC mentee was to implement varlink support to libnmstate functions which enables nmstate to used by other programming languages and systems.


## Progress
I was able start working on this tasks in mid of community bonding period. During this GSoC period I learnt alot about open source community and approches in development.

Below are patches I worked to understand the project code base (Before community bonding period).

* [PR #953](https://github.com/nmstate/nmstate/pull/953) [Merged] fix for [Issue #935](https://github.com/nmstate/nmstate/issues/935)

* [PR #1030](https://github.com/nmstate/nmstate/pull/1030) [Merged] fix for [Issue #1020](https://github.com/nmstate/nmstate/issues/1020)
 
 Following are links for the implementing varlink support

 * Implementing varlink support for libnmstate [PR #1270](https://github.com/nmstate/nmstate/pull/1270) [Merged]

 * Implemented systemd service for nmstate-varlink [PR #1271](https://github.com/nmstate/nmstate/pull/1271) [Merged]

 * Updated manpage for nmstate-varlink [PR #1297](https://github.com/nmstate/nmstate/pull/1297) [Merged]

 * Added documentation for nmstate-varlink service in ```nmstate.io``` [PR #44](https://github.com/nmstate/nmstate.github.io/pull/44)

 I have also written blog post under fedora community blog post about the implementation of varlink in nmstate and about my experience during the implementation as mentee. 
 
 * [Blog post](https://communityblog.fedoraproject.org/implementation-of-varlink-support-for-libnmstate-gsoc20-nmstate-project/)

## To do
Additionally task to be completed is improve kubernetes-nmstate to support varlink implementation in nmstate.