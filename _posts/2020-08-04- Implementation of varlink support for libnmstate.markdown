---
layout: post
title:  "Implementation of varlink support for libnmstate"
date:   2020-08-04 18:20:01 +0530
categories: Fedora GSoC Nmstate 
---
### [Click to read Fedora Community blog post][blog_link]

This blog is about the varlink implementation in nmstate and my experience in this during this period. As a computer science enthusiast I’m interested in researching new topics. This project is my first experience in open source development has been a challenging experience. The project aims to enable libnmstate to be used by other programming languages, systems which don’t support python and via remote connections. I have also included some links which I referred to. I hope it will be helpful for students like me.

## About nmstate and varlink
Nmstate is a python library that manages the networking setting of the host using the NetworkManger to apply the configuration. Nmstate also provides a command line tool called nmstatectl. Varlink is a simple protocol where all messages are encoded in JSON format. For varlink integration in specific programming languages it only requires the JSON support and socket communication.

## Implementation of varlink in libnmstate
In the current implementation libnmstate functions can be accessed with varlink stdin/out and varlink client. Nmstate methods and errors are defined in format to support future scalability in networking state schema and minimizing the complexity. Structure is defined in the io.nmstate.valink interface file and also interface address defined as io.nmstate. The interface file can be accessed using the following command.

All function methods and error returns with a list of logs include debug or higher level logs. The interface file can be accessed using the following command

```bash
$ varlink help unix:/run/nmstate.so/io.nmstate
```

Defined functions are called with the interface address and should be capitalized. Passing value via varlink stdio/out should be in JSON string format. 

libnmstate show function example:

```bash
$ varlink call unix:/run/nmstate.so/io.nmstate.Show
```

Using varlink resolver : $ varlink call io.nmstate.Show


libnmstate apply function example:

To support the varlink python package version 29.0.0 format of passing arguments to methods had to change. The arguments are passed under arguments key as json object.

```bash
$ varlink call unix:/run/nmstate.so/io.nmstate.Apply '{“arguments”: {"desired_state": {"interfaces": [{"name": "foo", "state": "up", "type": "dummy", “ipv4”:{“enabled”: false}, “ipv6”: {“enabled”: false}}]}, “save_to_disk”: true } }’ 
```

## Varlink client in python language
Functions can also be accessed using the varlink client implementation. Currently varlink supports client implementation in Python, C, Go, Java and Rust languages. Follow the documentation for new language binding.Varlink python package only supports for python3.

```bash
$ pip3 install "varlink>=29.0.0"
OR
$ dnf install python3-varlink -y
```

```python
import varlink

with varlink.Client("unix:/run/nmstate.so") as client:
    with client.open("io.nmstate") as nmstate:
        state = nmstate.Show()
        print(state)
In the current implementation nmstate-varlink service supports only file path Unix address. Uses nmstate command-line tool nmstatectl to initiate the service.
```

```bash
$ nmstatectl varlink /run/nmstate.so &
Users can use bridge mode for remote connection and activation mode to initiate the service for specific operations because it creates a temporary socket file connection.
```
```bash
S varlink --activate='nmstatectl varlink $VARLINK_ADDRESS' call io.nmstate.Show
```
## Issues faced during the development

Varlink interface definition syntax is easy to understand but difficult to debug syntax errors. In the beginning the interface syntax mistakes were difficult to identify with the complex nmstate state schema structure. To validate the interface file syntax, I used the varlink stdin/out help function. 

Some simple implementations failed during the first two weeks which caused delay. The bug was not documented so I had to go through the source code and try previous versions.
When integrating with rpm package varlink dependency failed because I used the varlink pypi package instead of rpm package. This issue also caused time and I had to refer to different documents and posts from the fedora community and stackoverflow. Creating a copr repository for the varlink latest pypi package(30.3.0) also failed.
Knowing the difference of package versions and minimum versions that support the implementation will save time.

## What I learned during development 

Testing : This was my first time implementing test cases. It was easy to understand syntax with pytest documentation. I also learn about different test cases implementation and about fixtures. Learned what is pylint, flake8 and black.

CI : CI is a popular topic during this project. I was able to learn the basics about CI and about travis. I was able use this knowledge for my academic projects which was very helpful in pandemic (I used github actions). 

Containers : Before this project I had a basic understanding about containers but with this project I was able get hands-on experience. With podman tutorial I familiarized with basic commands, operations and creating containerfile. It was interesting to me that we can create network interfaces in containers. I’m also trying to use containers in my future projects and learn more.

Rpm packaging and copr repository : I’m new to packaging link_1 and link_2 are useful documentation with every detail for a beginner. I learned how to work with spec files, RPM macros and scriptlets. This helped me in understanding copr repositories and I had to create a copr repository for varlink dependency.   

Systemd services : I have created a systemd service for an academic project (aim was to create a startup application) just by modifying a few lines. In this project I learned about systemd unit files and the options. It is long documentation


[blog_link]: https://communityblog.fedoraproject.org/implementation-of-varlink-support-for-libnmstate-gsoc20-nmstate-project/