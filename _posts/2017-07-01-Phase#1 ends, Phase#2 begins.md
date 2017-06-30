---
layout: post
title: Phase#1 ends Phase#2 begins
comments: true
permalink: /:title
image: ''
date:   2017-07-01 00:02:50
tags:
- GSoC
description: 'Phase#1 ends Phase#2 begins'
categories:
- GSoC
serie: learn


---
Hello World!

The first phase of GSoC is ended now and today I got the mail from Google stating "I have passed my first evaluation". I was so happy reading the mail(with my mentor's good feedback) as it will be my first ever earning.

I should also have posted a blog post last week as per my plan but I missed it as my OS had some problem and I had to clean install my Operating System. This ruined so much of my time in setting up my system. Also, Tammo was away for some days and creating an image in python-casacore was giving me some errors. Thanks to .travis.yml because of which I knew where the problem was. Actually, I hadn't compiled casacore with data packages. I compiled it again with data packages enabled and it worked like charm. In the meantime, I learned quite a bit of pybind11 which was proposed to replace boost.python in the coming days.

Now, coming to the project, [PR#97](https://github.com/casacore/python-casacore/pull/97) failed with Python 3.5 on Travis. More specifically whenever I used `iter` in tables, it was giving me an error(`RuntimeError: Invalid Table operation: SetupNewTable /root/ttable.py_tmp.tab1 is already opened (is in the table cache)`). It was a bug in casacore's end. This week, I will try to fix that. Moreover, I wrote the tests for `functionals`([PR#101](https://github.com/casacore/python-casacore/pull/101))  which got merged. The functionals module looked good to me and didn't have any boilerplate. The total coverage increased  9.3% by adding tests for functionals.

Although, I am not supposed to solve that bug(the one which gave an error in python3.5) in casacore but to increase my skillset in C++ codebase and as I  can give even some more time to the project, I am willing to solve the bug. I am still a newbie to C++ codebase, and understanding casacore's c++ codebase is quite difficult to me. I am trying to get familiar with the codebase and it will take some time.Simon suggested me to remove the iterator call in `TableCache.h` and see what happens, which I will try this week. Also, I will learn how casacore's native objects are converted into python-like objects by playing around casacore/python. And I forgot to mention the main part, I will be writing tests for `images` module this week.

So, in summary, my next week work will be:

* Write tests for `images`.
* learn how casacore/python is implemented.
* try to fix the bug in casacore.
* learn more pybind11 and CMake.



