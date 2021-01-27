# Google Summer of Code 2021
List of project ideas for students applying to the Google Summer of Code program in 2021 (GSoC 2021).

## Timeline

Until March 9, 2021 we won't know if we will have been accepted to be part of GSoC.

Please always refer to the official timeline: https://summerofcode.withgoogle.com/how-it-works/#timeline

## Application Process

0. Get familiar with GSoC

First of all, and if you have not done that yet, read the student guide which will allow you to understand all this process and how the program works overall:

[What is Google Summer of Code?](https://google.github.io/gsocguides/student/)

Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.


1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available matrix, telegram or discord channels. We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!

2. Fill out the application form

[Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal)

## Project Ideas


### Embedding Julia (Julia Loader)

Skills: C

Description:
...

Resources:
 - Julia Embedding Manual: https://docs.julialang.org/en/v1/manual/embedding/
 - Julia Dependency in CMake: https://github.com/JuliaInterop/libcxxwrap-julia/blob/master/FindJulia.cmake


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

## Find Us

Telegram:
<a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

Discord: 
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

Matrix (bridged with Telegram):
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>
