---
title: Requirements to productionize the datakit
author: Danny Morris
date: '2021-03-04'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

### Datakit Q&A

**Q: What environment resources will be needed to run the datakit codebase?**

A: The datakit codebase will run on a [physical/virtual] machine. The environment will need Python version 3.X and some third-party libraries including [list of libraries].

**Q: What event will trigger the deployment and execution of the datakit codebase?**

A: The datakit code will run at [insert time] each day.

**Q: Will the datakit codebase need to be deployed to another machine for execution?**

A: If using a physical machine, the code will need to be deployed from the main branch of the GitHub repository to the physical machine using Git. If using a virtual machine, such as GitHub Actions, the code does not need to be deployed to another location.

**Q: How will the datakit codebase be executed?**

A: Shell script