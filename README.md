命名规则相关
=======================
1、\*\_t结尾的变量可以理解为type/typedef的缩写，表示它是通过typedef定义的，而不是其它数据类型。

2、关于下划线开头的变量与函数，比如_error_print、struct \_modbus{}.
知乎上的回答：

——“某优雅语言我不太懂，但至少在C/C++里，标识符若以下划线开头，一般是在告诉你，这个东西，你不应该直接使用。”

——“标准规定单下划线加大写字母和双下划线开头的标识符都是预留给实现/扩展的，可移植的用户代码不该直接使用它们，也不该自行定义这种标识符。
反过来说，这也相当于鼓励编译器尽量用这些标识符做实现细节，以避免和用户代码的标识符冲突。”


A groovy modbus library
=======================

[![Build Status](https://travis-ci.org/stephane/libmodbus.svg?branch=master)](https://travis-ci.org/stephane/libmodbus)

Overview
--------

libmodbus is a free software library to send/receive data with a device which
respects the Modbus protocol. This library can use a serial port or an Ethernet
connection.

The functions included in the library have been derived from the Modicon Modbus
Protocol Reference Guide which can be obtained from Schneider at
[www.schneiderautomation.com](http://www.schneiderautomation.com).

The license of libmodbus is *LGPL v2.1 or later*.

The documentation is available as manual pages (`man libmodbus` to read general
description and list of available functions) or Web pages
[www.libmodbus.org/documentation/](http://libmodbus.org/documentation/). The
documentation is licensed under the Creative Commons Attribution-ShareAlike
License 3.0 (Unported) (<http://creativecommons.org/licenses/by-sa/3.0/>).

The official website is [www.libmodbus.org](http://www.libmodbus.org).

The library is written in C and designed to run on Linux, Mac OS X, FreeBSD and
QNX and Windows.

Installation
------------

You will only need to install automake, autoconf, libtool and a C compiler (gcc
or clang) to compile the library and asciidoc and xmlto to generate the
documentation (optional).

To install, just run the usual dance, `./configure && make install`. Run
`./autogen.sh` first to generate the `configure` script if required.

You can change installation directory with prefix option, eg. `./configure
--prefix=/usr/local/`. You have to check that the installation library path is
properly set up on your system (*/etc/ld.so.conf.d*) and library cache is up to
date (run `ldconfig` as root if required).

The library provides a *libmodbus.pc* file to use with `pkg-config` to ease your
program compilation and linking.

If you want to compile with Microsoft Visual Studio, you need to install
<https://github.com/chemeris/msinttypes> to fill the absence of stdint.h.

To compile under Windows, install [MinGW](http://www.mingw.org/) and MSYS then
select the common packages (gcc, automake, libtool, etc). The directory
*./src/win32/* contains a Visual C project.

To compile under OS X with [homebrew](http://mxcl.github.com/homebrew/), you
will need to install the following dependencies first: `brew install autoconf
automake libtool`.

Documentation
-------------

The documentation is available [online](http://libmodbus.org/documentation) or
as manual pages after installation.

The documentation is based on
[AsciiDoc](http://www.methods.co.nz/asciidoc/).  Only man pages are built
by default with `make` command, you can run `make htmldoc` in *doc* directory
to generate HTML files.

Testing
-------

Some tests are provided in *tests* directory, you can freely edit the source
code to fit your needs (it's Free Software :).

See *tests/README* for a description of each program.

For a quick test of libmodbus, you can run the following programs in two shells:

1. ./unit-test-server
2. ./unit-test-client

By default, all TCP unit tests will be executed (see --help for options).

It's also possible to run the unit tests with `make check`.

To report a bug or to contribute
--------------------------------

See [CONTRIBUTING](CONTRIBUTING.md) document.
