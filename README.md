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

- You're committing to a project and we may ask you to publicly publish your weekly progress on it.
- It's the first year Metacall is joining the GSoC program and we will ask you to give feedback on our mentorship and management continuously.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't give any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser **without downloading anything locally**.

You can also ask for a review anytime to the community or mentor candidates before the student application deadline. It's much easier if you get feedback early than to wait for the last moment.
  

## Project Ideas

### Embedding LLVM (LLVM Loader)

Skills: C++

Description:
The LLVM Project is a collection of modular and reusable compiler and toolchain technologies. Implementing LLVM into MetaCall will allow languages which have LLVM backend or can compile to LLVM IR. This will provide support to other loaders in the future like C/C++ Loader that can be implemented with `clang`, a frontend for LLVM.

Resources:
 - LLVM Embedding Manual: https://llvm.org/docs/CMake.html#embedding-llvm-in-your-project
 - LLVM Interpreter Example for Dynamic Compilation: https://github.com/llvm/llvm-project/blob/main/llvm/tools/lli/lli.cpp
 - How to list functions in LLVM (for introspection): https://github.com/mull-project/mull/blob/35f83655b04341b6260c5358168c4ac2da7bd86d/lib/Rust/RustTestFinder.cpp#L108

### Embedding Julia language (Julia Loader)

Skills: C, C++ (optional) and Julia (at least its type system)

Description:  
Julia is a modern programming language which features performance nearly as fast as C while still being adequate to the scientific community's rapid prototyping needs. Julia has a C api that Metacall could use to connect it with other languages than C/C++ with less effort.

Resources: 
 - Julia Embedding Manual: https://docs.julialang.org/en/v1/manual/embedding/
 - Julia Dependency in CMake: https://github.com/JuliaInterop/libcxxwrap-julia/blob/master/FindJulia.cmake

### Embedding Formality Proof Assistant (Formality Loader)

Skills: JavaScript

Description:  
Formality is a modern programming language that allows the developer to write formal proofs to validate the code. MetaCall has already very good support for JavaScript and formality could be implemented on top of it due to it having a [JavaScript compiler](https://github.com/moonad/FormCoreJS/blob/master/FmcToJs.js). The already implemented TypeScript Loader can be an example to follow due to TypeScript being also compiled to JavaScript. Applications would benefit from calling Formality with MetaCall, getting easy access to formal verification without having to reimplement much of the business logic and being able to verify single functions easily.

Resources:
 - Formality GitHub Repository: https://github.com/moonad/Formality
 - Formality JavaScript Backend: https://github.com/moonad/Formality/tree/master/bin/js
 - MetaCall TypeScript Loader (can be used as example to implement the Formality Loader): https://github.com/metacall/core/tree/develop/source/loaders/ts_loader

### Cross-Platform Builds

Skills: C/C++, Guix, DevOps

Description:
MetaCall has multiple runtimes embedded on it and one of its objectives is to be as cross platform as possible. Each runtime has its own dependencies which create a huge dependency tree sometimes. This is a big complexity that is difficult to handle. Our first approach was to Dockerize all dependencies, building them manually, taking care of `LDFLAGS` in order to make the distributable portable at the same time. After this, we tried Guix to implement our build system and we achieved to compile MetaCall completely and make it completely self-contained (in Linux for amd64). This allows MetaCall to be installed even in a BusyBox and work properly without any other system dependency. We have started to support cross-platform builds with Guix but the development has stalled. The objective of this task is to achieve cross-platform builds for Linux, Windows and MacOs, and multiple hardware architectures. Guix supports cross-compiling but it is sometimes restricted due to its nature. One option we propose is to override the `gnu-build-system` of Guix by using Zig compiler and allow Cross-Compiling by means of its frontend. But, there are many other options to do it and we are open to them. Maybe if it can be achieved with a different package manager we are open to it too.

Resources:
 - Initial Docker Cross-Platform Build Approach: https://github.com/metacall/distributable/tree/feature/build-scratch/linux
 - First steps in Cross-Platform Build for Guix: https://github.com/metacall/distributable/tree/feature/build-guix-cross
 - Base implementation of Cross-Platform support in `metacall/distributable`: https://github.com/metacall/distributable/blob/f14cbdcfe3bcb85e0331172e0dbb512e2f21350a/Makefile#L31 and https://github.com/metacall/distributable/blob/f14cbdcfe3bcb85e0331172e0dbb512e2f21350a/scripts/build.sh#L23
 - Guix Build Options Documentation: https://guix.gnu.org/manual/en/html_node/Additional-Build-Options.html
 - Cross-compiling with Zig: https://andrewkelley.me/post/zig-cc-powerful-drop-in-replacement-gcc-clang.html

### CLI Plugin Support

Skills: C++, NodeJS (optional)

Description: 
MetaCall Core itself is based on an extensible plugin system architecture. This means that MetaCall is built on top of plugins that load other plugins. We can use this to extend any software with a plugin system easily, including MetaCall CLI itself. Providing plugin support in the MetaCall CLI will allow you to easily extend the REPL commands and add extra features to all the runtimes. For example, [the next task](https://github.com/metacall/gsoc-2021/blob/main/README.md#cli-security-through-seccomp-sandboxing) can be completely implemented with a plugin if MetaCall would have support for C/C++ Loader. The MetaCall CLI will have a path where all plugins are stored and those will be loaded and populated to the REPL. Some examples of plugins that can be implemented are the command `serve`, which can implement a HTTP server with NodeJS, to serve locally the functions loaded by MetaCall. Another plugin can be improving the REPL history and visualization by means of the REPL package of NodeJS.

Resources:  
- MetaCall CLI Source: https://github.com/metacall/core/tree/develop/source/cli/metacallcli
- MetaCall CLI Install: https://github.com/metacall/install
- NodeJS HTTP: https://nodejs.org/api/http.html
- NodeJS REPL: https://nodejs.org/api/repl.html

### CLI Security Through `seccomp` (Sandboxing)

Skills: C/C++

Description:
Modern runtimes like Deno provide a command line interface for allowing / restricting capabilities and sandbox the execution of the code. We want to provide a similar approach but based on `libseccomp`. This approach will provide MetaCall CLI a standard system for filtering system calls independently of the language being executed. This will provide a safe sandboxing primitives that can be shared between runtimes at system call level. As a result MetaCall will be able to be executed safely without need to use Docker or any other virtualization tool.

Resources:
 - `libseccomp` GitHub Repository: https://github.com/seccomp/libseccomp
 - Example of usage for `libseccomp`: https://github.com/gebi/teach-seccomp/blob/master/step-2/example.c
 - Example of CMake find script for `libseccomp`: https://webkit-search.igalia.com/webkit/source/Source/cmake/FindLibseccomp.cmake
 - MetaCall CLI Source: https://github.com/metacall/core/tree/develop/source/cli/metacallcli
 - Deno Permission List: https://deno.land/manual/getting_started/permissions#permissions-list

### Packaging .NET Core with Guix (NonGuix)

Skills: Guix / Guile

Description:
Guix is a reproducible package manager and Operative System which is used by MetaCall to implement the build system. Guix does not allow to implement binary distributions and this restricts the support for packages that can be bootstrapped. The .NET Core infrastructure uses a seed compiler (binary) to build itself so it cannot be packaged by Guix. It is possible to use NonGuix which provides `binary-build-system`, which reproduces the style of Nix for distributing packages (it downloads the binaries and uses patchelf to relink the binaries). MetaCall can use this feature to implement support for .NET Core in the distributable.

Resources:
 - Existing issue related to the task in `metacall/distributable`: https://github.com/metacall/distributable/issues/1
 - NonGuix GitLab Repository: https://gitlab.com/nonguix/nonguix

### PyPy Loader with Benchmarks against CPython (Python Loader)

Skills: C/C++

Description:
PyPy is a fast, compliant alternative implementation of Python based on Just-In-Time compilation. Implementing it in MetaCall can provide higher performance which can benefit in faster execution of code, which is very important in environments like Cloud Computing or FaaS. The task will be to implement support to PyPy, and create benchmarks to document the performance improvements.

Resources:
 - PyPy Official Web: https://www.pypy.org/
- Embedding PyPy: https://doc.pypy.org/en/improve-docs/embedding.html
 - Example of MetaCall Benchmarks for Python Loader and Python C API: https://github.com/metacall/core/tree/develop/source/benchmarks/metacall_py_call_bench and https://github.com/metacall/core/tree/develop/source/benchmarks/metacall_py_c_api_bench

### Embedding Java and Scala (Loaders)

Skills: C/C++, Java

Description:  
Java Native Interface (JNI) is a foreign function interface programming framework that enables code running in a Java virtual machine (JVM) to call and be called by native applications, Metacall in this case. Currently there's a Java port using SWIG but we want to get rid of SWIG as a dependency and completely use JNI.

Resources:  
 - Java Native Interface: https://docs.oracle.com/javase/8/docs/technotes/guides/jni/
 - Java port using SWIG: https://github.com/metacall/core/tree/master/source/ports/java_port
 - Scala port: https://github.com/metacall/core/tree/master/source/ports/scala_port

### Implement an Error Handling System

Skills: C

Description:  
MetaCall has a log system but it does not support proper error handling yet. This means that if a function call, script loading or any other Core functionality fails, it is printed to the output medium but it does not return an error. This is very problematic and makes the API very poor. The design is already defined to support this feature (for example, many functions return `int` to verify if the result was correct, and after the error handling system is implemented, it will return an error status). The error handling must not be implemented with `setjmp` and `longjmp` because MetaCall must be stable among runtimes and this kind of error handling can be very problematic to runtimes that modify the stack as coroutine based languages like Golang. This implementation will modify the MetaCall C API and introduce a new error status for each function. We will also need a mechanism to create new errors, retrieve the last error of the system and clear that error which must be thread safe. The internal representation of the error can be implemented in the `reflect` system so we can propagate the error handling to the Loaders, so for example, we can throw an exception in Python and catch it on NodeJS.

Resources:  
 - N-API Error Handling: https://nodejs.org/api/n-api.html#n_api_napi_get_last_error_info
 - Python Error Handling: https://docs.python.org/3/c-api/exceptions.html#exception-handling

### Jupyter MetaCall Kernel

Skills: C/C++ at least to interact with Metacall Core

Description:  
Kernels are programming language specific processes that run independently and interact with the Jupyter Applications and their user interfaces. The student will have to decide which approach to consider with the objective of running different code snippets in different cells on a jupyter notebook using metacall.

Additional information (if there's enough time left):  
To make the process of writing in different programming languages throughout the jupyter notebook easier, a language inference process can be added to avoid forcing the user to specify which language is using on each cell with libraries such as [linguist](https://github.com/github/linguist) or [guesslang](https://github.com/yoeo/guesslang).

Resources:
 - Jupyter architecture: https://jupyter.readthedocs.io/en/latest/projects/architecture/content-architecture.html
 - Kernels: https://jupyter-client.readthedocs.io/en/latest/kernels.html#kernels
 - Wrapper kernels: https://jupyter-client.readthedocs.io/en/latest/wrapperkernels.html
 - List of existing kernels (examples) https://github.com/jupyter/jupyter/wiki/Jupyter-kernels

## Find Us

Telegram:
<a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

Discord: 
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

Matrix (bridged with Telegram):
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>
