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

These awesome three months of summer spent developing for python-casacore under Google Summer of Code, have filled me with great zeal and zest. The adventurous journey of thousand lines of code comes to an end.  This entire project was quite informative and filled me with lots of good experiences and knowledge. I thank [*OpenAstronomy*](http://openastronomy.org/) organization for accepting my GSoC proposal and my mentor [*Tammo Jan Dijkema*](https://github.com/tammojan)  for helping me throughout this project.

As per the requirement of GSoC, this article consists of a brief description of the work i have done, and the things that could not be done, what is left to do, what are future plans of the project, links to works that were merged and links to patches that were not.

Most of the tasks mentioned in the [proposal](https://storage.googleapis.com/summerofcode-prod.appspot.com/gsoc/core_project/doc/4875372463128576_1491143172_OpenAstronomyGSoC-2017Application3.pdf?Expires=1502555575&GoogleAccessId=summerofcode-prod%40appspot.gserviceaccount.com&Signature=otv3V%2BFfcEqN3FXYjzUa084wvjofrfetgKO75IXGa66oipuayB%2Bt5IA6mEd3zB9YO0ySrD6rcAOGbKM%2B31An5h45ZIgVVr%2BAh%2BOWAyxEDyiFNF9%2BVdKK7zGyhWG2bhrj0rrISBNso4DWEpbcXoZzrActQYb%2BOEhT6PxsEpTfAZLW1G2HO4JVlrMgtWUbAII2Z8U%2FD469cXU%2B7rUzJHCoZuQI18MLI%2BxJgBy8ibg9QVb2L9aWq5Oz3q27p4NoVsCzhhlnWSRybon8UhJgiH160oNKrYqyNC5a6OOI3J%2BfIAsT3zSn%2Bpq7v5qzOglEsXWVuDdoPY4C7kaqy1uZPiKLBQ%3D%3D) were discussed and worked upon. 

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

[porting python bindings from using boost::python to pybind11](https://github.com/shibasisp/python-casacore/tree/pybind11)(Not yet completed.)



Forked Branch: https://github.com/shibasisp/python-casacore



The momentum gained through this project is a great moral booster for me and I wish this momentum will drive my curiosity to keep learning more in future and the open source technologies will flourish with their full potential and thrive to its zenith.











