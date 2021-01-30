# Google Summer of Code 2021
List of project ideas for students applying to the Google Summer of Code program in 2021 (GSoC 2021).

## Timeline

Until March 9, 2021 we won't know if we will have been accepted to be part of GSoC.

Please always refer to the [official timeline](https://summerofcode.withgoogle.com/how-it-works/#timeline). 
  
## Application Process

#### 0. Get familiar with GSoC

First of all, and if you have not done that yet, read [the student guide](https://google.github.io/gsocguides/student/) which will allow you to understand all this process and how the program works overall. Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.  
  
#### 1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available [contact channels](https://github.com/metacall/gsoc-2021#find-us). We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!  
  
#### 2. Understand that

- You're commiting to a project and we may ask you to publicly publish your weekly progress on it.
- It's the first year Metacall is joining the GSoC program and we will ask you to give feedback on our mentorship and management continuously.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't give any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser **without downloading anything locally**.

You can also ask for a review anytime to the community or mentor candidates before the student application deadline. It's much easier if you get feedback early than to wait for the last moment.
  

## Project Ideas


### Embedding Julia language (Julia Loader)

Skills: C, C++ (optional) and Julia (at least its type system)

Description:  
Julia is a modern programming language which features performance nearly as fast as C while still being adequate to the scientific community rapid prototyping needs. Julia has a C api that Metacall could use to connect it with other languages than C/C++ with less effort.

Resources: 
 - Julia Embedding Manual: https://docs.julialang.org/en/v1/manual/embedding/
 - Julia Dependency in CMake: https://github.com/JuliaInterop/libcxxwrap-julia/blob/master/FindJulia.cmake


### Jupyter Metacall kernel

Skills: C/C++ at least to interact with Metacall core

Description:  
Kernels are programming language specific processes that run independently and interact with the Jupyter Applications and their user interfaces. The student will have to decide which approach to consider with the objective of running different code snippets in different cells on a jupyter notebook using metacall.

Additional information (if there's enough time left):  
To make the process of writing in different programming languages throughout the jupyter notebook easier, a language inference process can be added to avoid forcing the user to specify which language is using on each cell with libraries such as [linguist](https://github.com/github/linguist) or [guesslang](https://github.com/yoeo/guesslang).

Resources:
 - Jupyter architecture: https://jupyter.readthedocs.io/en/latest/projects/architecture/content-architecture.html
 - Kernels: https://jupyter-client.readthedocs.io/en/latest/kernels.html#kernels
 - Wrapper kernels: https://jupyter-client.readthedocs.io/en/latest/wrapperkernels.html
 - List of existing kernels (examples) https://github.com/jupyter/jupyter/wiki/Jupyter-kernels


### Embedding LLVM (LLVM Loader)

Skills: C++

Description:
...

Resources:
 - LLVM Embedding Manual: https://llvm.org/docs/CMake.html#embedding-llvm-in-your-project
 - LLVM Interpreter Example for Dynamic Compilation: https://github.com/llvm/llvm-project/blob/main/llvm/tools/lli/lli.cpp
 - How to list functions in LLVM (for introspection): https://github.com/mull-project/mull/blob/35f83655b04341b6260c5358168c4ac2da7bd86d/lib/Rust/RustTestFinder.cpp#L108

### Embedding Formality Proof Assistant (Formality Loader)

Skills: JavaScript

Description:
...

Resources:
 - Formality GitHub Repository: https://github.com/moonad/Formality
 - Formality JavaScript Backend: https://github.com/moonad/Formality/tree/master/bin/js
 - MetaCall TypeScript Loader (can be used as example to implement the Formality Loader): https://github.com/metacall/core/tree/develop/source/loaders/ts_loader

### CLI Security Through `seccomp` (Sandboxing)

Skills: C/C++

Description:
Modern runtimes like Deno provide a command line interface for allowing / restricting capabilities and sandbox the execution of the code. We want to provide a similar approach but based on `libseccomp`. This approach will provide to MetaCall CLI a standard system for filtering system calls independently of the language being executed. This will provide a safe sandboxing primitives that can be shared between runtimes at system call level. As a result MetaCall will be able to be executed safely without need to use Docker or any other virtualization tool.

Resources:
 - `libseccomp` GitHub Repository: https://github.com/seccomp/libseccomp
 - Example of usage for `libseccomp`: https://github.com/gebi/teach-seccomp/blob/master/step-2/example.c
 - Example of CMake find script for `libseccomp`: https://webkit-search.igalia.com/webkit/source/Source/cmake/FindLibseccomp.cmake
 - MetaCall CLI Source: https://github.com/metacall/core/tree/develop/source/cli/metacallcli
 - Deno Permission List: https://deno.land/manual/getting_started/permissions#permissions-list

### Cross-Platform Builds with Guix

Skills: Guile

Description:
...

Resources:
 - Base implementation of Cross-Platform support in `metacall/distributable`: https://github.com/metacall/distributable/blob/f14cbdcfe3bcb85e0331172e0dbb512e2f21350a/Makefile#L31 and https://github.com/metacall/distributable/blob/f14cbdcfe3bcb85e0331172e0dbb512e2f21350a/scripts/build.sh#L23
 - Guix Build Options Documentation: https://guix.gnu.org/manual/en/html_node/Additional-Build-Options.html
 - Cross-compiling with Zig: https://andrewkelley.me/post/zig-cc-powerful-drop-in-replacement-gcc-clang.html

### Packaging NetCore with Guix (NonGuix)

Skills: Guile

Description:
...

Resources:
 - Existing issue related to the task in `metacall/distributable`: https://github.com/metacall/distributable/issues/1
 - NonGuix GitLab Repository: https://gitlab.com/nonguix/nonguix

### Pyston Loader with Benchmarks against CPython (Python Loader)

Skills: C++

Description:
Pyston is an experimental JIT for Python which follows the same C API as CPython. Implementing it in MetaCall can provide higher performance which can benefit in faster execution of code, which is very important on enviroments like Cloud Computing or FaaS. The task will be to implement support to Pyston based on the Python Loader, and create benchmarks to document the performance improvements.

Resources:
 - Pyston GitHub Repository: https://github.com/pyston/pyston
 - Pyston Install Documentation: https://pyston.readthedocs.io/en/stable/INSTALLING/
 - Example of MetaCall Benchmarks for Python Loader and Python C API: https://github.com/metacall/core/tree/develop/source/benchmarks/metacall_py_call_bench and https://github.com/metacall/core/tree/develop/source/benchmarks/metacall_py_c_api_bench


### Embedding Java and Scala (loaders)

Skills: C/C++

Description:  
Java Native Interface (JNI) is a foreign function interface programming framework that enables code running in a Java virtual machine (JVM) to call and be called by native applications, Metacall in this case. Currently there's a Java port using SWIG but we want to get rid of SWIG as a dependency and completely use JNI.

Resources:  
 - Java Native Interface: https://docs.oracle.com/javase/8/docs/technotes/guides/jni/
 - Java port using SWIG: https://github.com/metacall/core/tree/master/source/ports/java_port
 - Scala port: https://github.com/metacall/core/tree/master/source/ports/scala_port


### Implement an error handling system (TBD)

Skills: C

Description:  
To be defined

Resources:  
 - ...


## Find Us

Telegram:
<a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

Discord: 
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

Matrix (bridged with Telegram):
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>
