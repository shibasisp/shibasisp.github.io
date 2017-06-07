---
layout: post
title: Community Bonding period coming to an end
comments: true
permalink: /:title
image: ''
date:   2017-05-27 00:01:50
tags:
- GSoC
description: ''
categories:
- GSoC
serie: learn


---

The acceptance marked the start of "Community Bonding Period", which in GSoC's terminology is a month for students to get acquainted with their mentors, explore the codebase of their organization and review the project's timeline so they can kick off coding when the "Coding period" starts.

The community bonding period is about to end in 3 days after this post. This is what I did in this period:

* Read the python-casacore docs and the codebase.


* Read `Effective Python` by Brett Slatkin and `Writing Idiomatic Python` by Jeff Knupp for learning pythonic way of writing python :smile:.
* Solved some small issues ([Issue#62](https://github.com/casacore/python-casacore/issues/62), [Issue#60](https://github.com/casacore/python-casacore/issues/60) ,[PR#86](https://github.com/casacore/python-casacore/pull/86)) and reported bugs([Issue#87](https://github.com/casacore/python-casacore/issues/87)) for python-casacore.

[Simon Perkin](https://github.com/sjperkins) proposed to use [pybind11](https://github.com/pybind/pybind11) instead of [Boost.Python](http://www.boost.org/doc/libs/1_58_0/libs/python/doc/) as it is a lightweight header-only library and its syntax are similar to Boost.Python whereas Boost.Python requires binary libraries. Also, I had a hard time while installing Boost.Python in my system and compiling my first program. However, we would do it after finishing other goals.


This is the first time in my life that I am working with a team to make something that will actually be used by someone. Though it will take a little time to learn to work with goals and timelines, but I guess this is what I am here to learn.

Community bonding period was fun, but now it's time to finalize mock-ups and bring them to life in the coding period.

In the end I would like to thank OpenAstronomy and my mentors to provide me with the amazing opportunity to work on this project.
