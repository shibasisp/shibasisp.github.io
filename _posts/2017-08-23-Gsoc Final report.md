---
layout: post
title: GSoC final report
comments: true
permalink: /:title
image: ''
date:   2017-08-23 00:03:56
tags:
- GSoC
description: GSoC final report
categories:
- GSoC
serie: learn


---

These awesome three months of summer spent developing for python-casacore under Google Summer of Code, have filled me with great zeal and zest. The adventurous journey of thousand lines of code comes to an end.  This entire project was quite informative and filled me with lots of good experiences and knowledge. I thank [*OpenAstronomy*](http://openastronomy.org/) organization for accepting my GSoC proposal and my mentor [*Tammo Jan Dijkema*](https://github.com/tammojan) and the community for helping me throughout this project.

As per the requirement of GSoC, this article consists of a brief description of the work i have done, and the things that could not be done, what is left to do, what are future plans of the project, links to works that were merged and links to patches that were not.

Most of the tasks mentioned in the [proposal](https://docs.google.com/document/d/1c8HlyVIIm97uhh3ig-dpKNGeM8UbDpyoRI3oHrBSPvs/edit) were discussed and worked upon. 

**Links to the major patch submissions:**

[Removed Compiler warnings](https://github.com/casacore/python-casacore/pull/86)

[wrote tests and improved code quality for utils](https://github.com/casacore/python-casacore/pull/89)

[fixed formatting and code cleanup for casacore.tables](https://github.com/casacore/python-casacore/pull/98)

[Added tests for casacore.tables](https://github.com/casacore/python-casacore/pull/114) (Some parts in the tests were commented as the tests were failing due to a [bug](https://github.com/casacore/casacore/issues/611) in casacore)

[Added tests for casacore.functionals](https://github.com/casacore/python-casacore/pull/101) 

[Corrected formatting and code cleanup for casacore.images](https://github.com/casacore/python-casacore/pull/107)

[Added tests for images.py and coordinates.py](https://github.com/casacore/python-casacore/pull/106)

[Improved code qualities for casacore.fitting](https://github.com/casacore/python-casacore/pull/109)

[Added tests for casacore.fittings](https://github.com/casacore/python-casacore/pull/110)

[Added tests and improved code quality for casacore.quanta](https://github.com/casacore/python-casacore/pull/113)

[Improved incomplete docs](https://github.com/casacore/python-casacore/pull/117)

[Added travis OSX support](https://github.com/casacore/python-casacore/pull/115/files)

**Bonus Work**

[porting python bindings from using boost::python to pybind11](https://github.com/shibasisp/python-casacore/tree/pybind11)



Forked Branch: [python-casacore](https://github.com/shibasisp/python-casacore)



The momentum gained through this project is a great moral booster for me and I wish this momentum will drive my curiosity to keep learning more in future and the open source technologies will flourish with their full potential and thrive to its zenith.











