---
layout: post
title: Using Conda as a build environment for Linux
---

When it comes to installing software programs and libraries on Linux, compiling from source code is a first-class citizen. I mean it's the most preferred way and has been there to save lots of time from software developers to meet the different requirements of different hardware/software configurations on a wide variety of Linux distributions. This process has its own challenges, especially in case of installing and satisfying the required dependencies, a task that can be quite nightmarish (of course not as bad as as the nostalgic [DLL hell](https://en.wikipedia.org/wiki/DLL_Hell) in Windows). It can get even worse when you don't have root access to install the dependencies, which happens every now and then in daily life of a computational researcher when he/she wants to do this on a remote cluster or a university supercomputer.

A potential solution to this issue is taking advantage of container technologies like [Docker](https://docs.docker.com/get-started/) or [Singularity](https://singularity.lbl.gov/quickstart), but what if we don't have access to these packages as well? True, the most trivial solution would be compiling all the dependencies also from source code, but you should go for it only if you have super "enough time" as it can be an endless task. This is something I did once to build [FreeFEM](https://freefem.org/) on an old cluster, and to be honest, it was something I will never go for that again because it required me to compile not only all the dependencies but the compilers as well (a process called "[Bootstrapping](https://en.wikipedia.org/wiki/Bootstrapping_(compilers))"). By the way, that was fun enough to be told later, and yes, I should write about it at some point.

So, is there any other option? Yes, there is. Although people know it as a virtual environment manager for Python, [Conda](https://docs.conda.io/en/latest/) can be used in a more generalized manner, and it can be a lifesaver for the aforementioned issue as it provides a fully isolated environment (like containers but without living directly on the kernel) to install the required libraries and compilers. Above this all, it's very easy to install Conda on a Linux system without the root privilege and any previous software dependency. Yes, what can be better than that?

Technically speaking, compiling things on a Conda environment can be considered as "pseudo-cross-compiling", a sub-category of "[cross-compiling](https://en.wikipedia.org/wiki/Cross_compiler)" (a common term you may frequently hear about in the field of embedded systems in which you compile a program on a system but run it somewhere else on a different architecture). But, I cannot describe pseudo-cross-compiling better than how the Anaconda team has documented it in [Anaconda compiler tools](https://docs.conda.io/projects/conda-build/en/latest/resources/compiler-tools.html), so I just quote the relevant part here:
> Anaconda's compilers for Linux are built with something called crosstool-ng. They include not only GCC but also a "sysroot" with glibc, as well as the rest of the toolchain (binutils). Ordinarily, the sysroot is something that your system provides, and it is what establishes the libc compatibility bound for your compiled code. Any compilation that uses a sysroot other than the system sysroot is said to be "cross-compiling." When the target OS and the build OS are the same, it is called a "pseudo-cross-compiler". This is the case for normal builds with Anaconda's compilers on Linux.

It's very cool, isn't it?

A couple of weeks ago, a colleague of mine asked me for a solution to install [OpenFOAM](https://openfoam.org/) on a cluster on which he didn't have root privilege. OpenFOAM has a straightforward [installation procedure from the source code](https://openfoam.org/download/source/) but the thing is it requires root privileges to install required dependencies, which is obviously not possible in this case. So, I tried Conda for the first time for this purpose, and indeed, it  worked like a charm for us. Yes, it was a bit challenging to make it work (which I should write about in a separate post), but it helped us to compile a complex software from scratch totally independent from the underlying OS and its configurations. In the next post, I will document the procedure in detail as an example of this approach.