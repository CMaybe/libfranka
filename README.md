# libfranka: C++ library for Franka Emika research robots

[![Build Status][travis-status]][travis]
[![codecov][codecov-status]][codecov]

With this library, you can control research versions of Franka Emika robots. See the [Franka Control Interface (FCI) documentation][fci-docs] for more information about what `libfranka` can do and how to set it up. The [generated API documentation][api-docs] also gives an overview of its capabilities.

## install

To build `libfranka`, install the following dependencies from Ubuntu’s package manager:
```
sudo apt install build-essential cmake git libpoco-dev libeigen3-dev
```
\
For Panda you need to clone:

```
git clone --recursive https://github.com/CMaybe/libfranka --branch 0.8.1 
cd libfranka
git submodule update
```
\
In the source directory, create a build directory and run CMake:

```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTS=OFF ..
cmake --build .
```
\
Optionally (but recommended), a libfranka Debian package can be built using the following command in the same directory:

```
cpack -G DEB
```
\
This creates libfranka-<version>-<architecture>.deb. This package can then be installed with:

```
sudo dpkg -i libfranka*.deb
```

## Setting up the real-time kernel
To control your robot using libfranka, the controller program on the workstation PC must run with real-time priority under a `PREEMPT_RT` kernel. If you're using Ubuntu 22.04, you can follow this [link](https://yogyui.tistory.com/entry/Linux-Real-Time-Ubuntu-2204-LTS).

## License

`libfranka` is licensed under the [Apache 2.0 license][apache-2.0].

[apache-2.0]: https://www.apache.org/licenses/LICENSE-2.0.html
[api-docs]: https://frankaemika.github.io/libfranka
[fci-docs]: https://frankaemika.github.io/docs
[travis-status]: https://travis-ci.org/frankaemika/libfranka.svg?branch=master
[travis]: https://travis-ci.org/frankaemika/libfranka
[codecov-status]: https://codecov.io/gh/frankaemika/libfranka/branch/master/graph/badge.svg
[codecov]: https://codecov.io/gh/frankaemika/libfranka
