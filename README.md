Set up Clang
============

[![Test](https://github.com/egor-tensin/setup-clang/workflows/Test/badge.svg)](https://github.com/egor-tensin/setup-gcc/actions?query=workflow%3ATest)

This is a GitHub action that sets up Clang & LLVM in your workflow run.

Use it in your workflow like this:

    - name: Set up Clang
      uses: egor-tensin/setup-clang@v1
      with:
        platform: x64

* `x64` is the default value for the `platform` parameter and can be omitted.
Use `x86` if you want to build 32-bit binaries.
* Set the `cygwin` parameter to `1` to set up Clang inside an existing Cygwin
installation (you can set up Cygwin itself using my action [setup-cygwin]).
* `cc` and `c++` executables are set up, pointing to the `clang` and `clang++`
executables.
Disable this by setting the `cc` parameter to `0`.

[setup-cygwin]: https://github.com/egor-tensin/setup-cygwin

API
---

| Input     | Value   | Default | Description
| --------- | ------- | ------- | -----------
| platform  | x64     | Yes     | Install the x86_64 toolchain.
|           | *Other* | No      | Install the i686 toolchain.
| cygwin    | *Other* | Yes     | Install native binaries.
|           | 1       | No      | Install Cygwin packages.
| cc        | 1       | Yes     | Set up `cc`/`c++` executables.
|           | *Other* | No      | Don't set up `cc`/`c++`.
| hardlinks | *Other* | Yes     | Cygwin: don't convert any symlinks.
|           | 1       | No      | Cygwin: convert symlinks in /usr/bin to hardlinks.

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

[LICENSE.txt]: LICENSE.txt
