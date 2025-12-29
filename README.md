Set up Clang
============

[![Test](https://github.com/egor-tensin/setup-clang/actions/workflows/test.yml/badge.svg)](https://github.com/egor-tensin/setup-clang/actions/workflows/test.yml)

This GitHub action sets up Clang & LLVM in your workflow run.

1. Installs either 32-bit or 64-bit Clang & LLVM on either Ubuntu or Windows.
2. Specify a version to install using the `version` parameter.

Use it in your workflow like this:

    - name: Set up Clang
      uses: egor-tensin/setup-clang@v1
      with:
        version: latest
        platform: x64

* `latest` is the default value for the `version` parameter and can be omitted.
* `x64` is the default value for the `platform` parameter and can be omitted.
Use `x86` if you want to build 32-bit binaries.
* `cc` and `c++` executables are set up, pointing to the `clang` and `clang++`
executables.
Disable this by setting the `cc` parameter to `0`.

API
---

| Input     | Value   | Default | Description
| --------- | ------- | ------- | -----------
| version   | latest  | ✓       | Install the latest version available in the repository.
|           | *any*   |         | Install a specific version if it's available (see below).
| platform  | x64     | ✓       | Install the x86_64 toolchain.
|           | *any*   |         | Install the i686 toolchain.
| cc        | 1       | ✓       | Set up `cc`/`clang`/`c++`/`clang++` executables.
|           | *any*   |         | Don't set up the executables.

| Output  | Example   | Description
| ------- | --------- | -----------
| clang   | clang-4.0 | `clang` binary name
| clangxx | clang++-7 | `clang++` binary name

Supported versions
------------------

Unless the `version` parameter value is "latest", the official LLVM repository
is used to make more versions available.
You can pass the version number as the `version` parameter value (`5.0`, `8`,
`9`, etc.), and this action will install the corresponding packages.

The `version` parameter value is not checked for being an available version for
the current distribution.
The supported versions for a particular distribution are those found in that
distro's repositories & those in the LLVM repository.
For example, you can find the list of available versions as of January 2023
below.

| `version` | Jammy | Noble
| --------- | ----- | -----
| 11        | ✓     |
| 12        | ✓     |
| 13        | ✓     |
| 14        | ✓     | ✓
| 15        | ✓     | ✓
| 16        | ✓     | ✓
| 17        | ✓     | ✓
| 18        | ✓     | ✓
| 19        | ✓     | ✓
| 20        | ✓     | ✓
| 21        | ✓     | ✓

This table should be updated periodically; it's a work-in-progress.
(Note to self: the supported versions are those found in [Ubuntu repos] and
the official [LLVM repos]).

[Ubuntu repos]: https://packages.ubuntu.com/
[LLVM repos]: https://apt.llvm.org/

On Windows, the `version` parameter is ignored.

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

[LICENSE.txt]: LICENSE.txt
