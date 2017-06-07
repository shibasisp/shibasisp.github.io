---
layout: post
title: 1st Week of GSoC
comments: true
permalink: /:title
image: ''
date:   2017-06-7 00:23:50
tags:
- GSoC
description: '1st week Review'
categories:
- GSoC
serie: learn


---
Hello, Everyone!

It's the completion of 1st week and in this post, I will tell you what I have done in this week and what I have planned to do in the coming weeks.

As per my timeline in the proposal, I should be removing all the compiler warnings in the first week. I didn't get much compilation warnings other than one i.e  python-casacore couldn't find boost library "boost_python". PR [#86](https://github.com/casacore/python-casacore/pull/86/files) fixed the warning.

Then I modified `substitute.py` code to look the more Pythonic. PR#[89](https://github.com/casacore/python-casacore/pull/89) did it. [Ger van Diepen](https://github.com/gervandiepen) had already written much of the tests for it. So, I didn't have to do much for it.

Now, I am dealing with `casacore.tables` which I had planned to do in my 3rd week. Working with the codebase, I realized that I need 2 weeks instead of one to complete this. I will be submitting the PR for `casacore.tables` by the end of this week.

The new version of casacore got released and some of my old PRs which were failing on Casacore-2.0 (as the fix in FunctionalProxy::setmasks (PR [casacore/casacore#327](https://github.com/casacore/casacore/pull/327), 11-Mar-2016) was not available in casacore-2.0) got merged. 
