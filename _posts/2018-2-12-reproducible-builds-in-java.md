---
layout: post
title: Reproducible Builds in Java
author: Maria Camenzuli
---

When it comes to software, we look at source code to learn and verify what an application will do when executed. However, the source code we read is not what will actually be executed by our computers. In the Java world, it is the Java bytecode that is produced by our compilers that eventually gets executed, normally after having been packaged into an archive. So when we are given code that has already been compiled and packaged, how can we verify that it is indeed the product of the source code we think produced it?

The answer to this is reproducible builds. A reproducible build is a deterministic function, that given our source code as input, will produce an executable artifact that is the same, byte for byte, every time it is run with the same input.

If you want to read more about reproducible builds, I suggest you take a look at [reproducible-builds.org](https://reproducible-builds.org/).