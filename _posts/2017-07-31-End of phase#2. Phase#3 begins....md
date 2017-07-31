---
layout: post
title: End of phase#2. Phase#3 begins...
comments: true
permalink: /:title
image: ''
date:   2017-07-15 00:17:34
tags:
- GSoC
description: End of phase#2. Phase#3 begins...
categories:
- GSoC
serie: learn


---

Hello World!

2nd evaluation is finished now and I have passed the evaluation. My college will be starting from tomorrow i.e August 1st after a 3 month long summer break and I have completed most of my work on this project. I can still give around 25-30 hours per week. As a bonus work, I am trying to port python-casacore from boost::python to pybind11. Well I have hinted you this in some of my earlier posts but I haven't told you formally. Have I?

boost::python works very well for python-casacore, but it has proven to be exceedingly annoying while building. It takes great care to ensure a fully consistent boost and python install and that python-casacore finds the right ones. Also, according to the [issue #96](https://github.com/casacore/python-casacore/issues/96) , [this](https://svn.boost.org/trac10/ticket/12516) bug of boost seems to affect casacore. It would be great to remove this headache.

**Why pybind11?**

Although there are many options to wrap casacore, but we have chosen pybind11 for wrapping. I don't know much about the other options but cython is one of the options. After watching [this](https://www.youtube.com/watch?v=_1MSX7V28Po) video, I really like it. One major benefit is that you can generate code for a python module file and check that into the repository so that the users don't even need cython to build python-casacore . It uses a python-like language to compile to these C/C++ modules. If I was starting writing python-bindings for casacore from scratch, I would probably use it. However, cython has a different mentality to wrapping classes than boost::python, and converting python-casacore over would require a massive undertaking. This would take a lot of work, and I'm not sure I want to do that. Things are fine wrapped the way they are, as we get massive amounts of code reuse with one python super class that works via duck-typing with many different types of sub-classes. When interacting with C++ classes, cython requires strong typing. [pybind11](https://github.com/pybind/pybind11) looks like an interesting alternative. It is modeled on boost::python, but implemented as a header-file only solution which we could embed in python-casacore. It uses C++11 features to achieve this. C++11 as a dependency won't be a major problem for casacore as in any way, however it will be a dependency in casacore 3.0(https://github.com/casacore/casacore/issues/580).

​										    **Cython**

| **Pros**                                | **Cons**                                 |
| --------------------------------------- | ---------------------------------------- |
| Generate standards compliant C++ code   | Wrappers can instantiate templates, but only explicitly. |
| Write wrapper in a python-like language | Strong typing in cython files required when interacting with c++. Either we add an additional layer of wrapping, or get a lot of duplicate code. |



​										**pybind11**

| **Pros**                                 | **Cons**        |
| ---------------------------------------- | --------------- |
| Minimal effort to port python-casacore, as the syntax is almost identical to boost::python | Requires C++11. |
| Header file only, can embed.             |                 |
| Python version binding is at compile time, no more need to get consistent boost::python and python versions linked to casacore. |                 |

I have found [this](https://github.com/davisking/dlib/issues/293) to be pretty useful resource for shifting from boost::python to pybind11 and hope to make it more updated and will post the updated conversion table from boost::python to pybind11 on my future posts.

