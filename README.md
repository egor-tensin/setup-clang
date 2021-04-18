Set up Clang
============

[![Test](https://github.com/egor-tensin/setup-clang/actions/workflows/test.yml/badge.svg)](https://github.com/egor-tensin/setup-clang/actions/workflows/test.yml)

This GitHub action sets up Clang & LLVM in your workflow run.

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
| platform  | x64     | ✓       | Install the x86_64 toolchain.
|           | *any*   |         | Install the i686 toolchain.
| cygwin    | *any*   | ✓       | Install native binaries.
|           | 1       |         | Install Cygwin packages.
| cc        | 1       | ✓       | Set up `cc`/`c++` executables.
|           | *any*   |         | Don't set up `cc`/`c++`.
| hardlinks | *any*   | ✓       | Cygwin: don't convert any symlinks.
|           | 1       |         | Cygwin: convert symlinks in /usr/bin to hardlinks.

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

[LICENSE.txt]: LICENSE.txt
