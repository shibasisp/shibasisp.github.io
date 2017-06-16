---
layout: post
title: 2nd Week of GSoC
comments: true
permalink: /:title
image: ''
date:   2017-06-16 00:23:50
tags:
- GSoC
description: '2nd week Review'
categories:
- GSoC
serie: learn


---
Hello World!

It's the completion of the 2nd week of GSoC. And as I mentioned in my [last post](/1st-week-of-GSoC), I have covered the `tables` module by now.

Let me give a quick intro of what `tables` module does .`tables` module is by far the most important part of python-casacore. Radio Antenna and radio receiver use to receive radio waves from the astronomical radio sources from the sky and generates a time series of many frequencies. The signals from these different antenna are combined by correlating them in a short time interval. If you want to know more about how the signals is correlated, you can refer to this [post](https://casper.berkeley.edu/astrobaki/index.php/Basic_Interferometry). Now, these data is handled in casacore via the table system and particularly, visibility data are stored in a CASA table known as a Measurement Set (MS).

I have submitted two PRs in this week, one for making the codebase clean and pythonic ([PR#98](https://github.com/casacore/python-casacore/pull/98)) and the other is for the tests for `tables` module([PR#97](https://github.com/casacore/python-casacore/pull/97)). `casacore.tables.msconcat` with concatTime=False and `casacore.tables.msregularize`methods are yet to be tested. Right now, the coverage of `tables` has been increased to around 70% and I believe that after testing the above two methods, the coverage will increase upto 80%+.

For the next week, I have planned to improve `casacore.functionals`, and would try to test the above two methods of `tables`.

