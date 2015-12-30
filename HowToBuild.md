# Build Steps #

## Precompiled Packages ##
If you want to try pyv8 ASAP, we suggest you use precompiled package for your platform.

Please downloads the precompiled [packages](http://code.google.com/p/pyv8/downloads/list) for Windows and Linux/Debian.

tocer also provide packages [(1)](http://aur.archlinux.org/packages.php?ID=36092) [(2)](http://aur.archlinux.org/packages.php?ID=36076) for [ArchLinux](http://www.archlinux.org/)

## Build the module ##
Just run the setup.py with **install** or **build** command

```
setup.py install
```

## Build the distribution ##
Just run the setup.py with **bdist** or **bdist\_wininst** command

```
setup.py bdist_wininst
```

# Third Party Library #

## Python ##
As the runtime and libraries, download and install [Python 2.5](http://www.python.org/download/) or later first.

set environment variable PYTHON\_HOME to the python root folder

## Boost ##
PyV8 use [boost::python](http://www.boost.org/doc/libs/release/libs/python/doc/) for interoperability, so, [download](http://www.boost.org/users/download/) the latest boost version and [build](http://www.boost.org/doc/libs/release/more/getting_started/) the library.

set environment variable BOOST\_HOME to the boost root folder

## Google V8 ##

**Please use PyV8's setup.py script to build Google V8, because PyV8 need RTTI and Exception support, check the following section for more detail**

Follow the [document](http://code.google.com/apis/v8/build.html) to download and build v8 engine as static library

set environment variable V8\_HOME to the v8 root folder

If you want to build v8 with GCC 4.x at x64 platform, you should compile v8 with PIC (Position-Independent Code) mode, and set the arch to x64 for scons.
```
export CCFLAGS=-fPIC
scons arch=x64
```
You may also need build Boost with '-fPIC' argument.
```
./bjam --clean
./bjam cxxflags=-fPIC
```

### Runtime Type Information and C++ Exception in v8 3.0 ###

From the v8 engine 3.0, the build script of v8 engine has disabled RTTI and Exception by default. It may save some bits of memory, but will broke the boost::python library and pyv8.

PyV8's setup.py will try to automatic patch V8's build scripts to enable RTTI and Exception supports.

So, please set V8\_HOME environment variable port to your V8 code, or let's PyV8's setup.py checkout a private build, before you make a clean build.

## Debug Mode ##
You could build Google v8 and PyV8 with debug mode, for more detail debug information.

  * Build v8 with debug mode
```
scons mode=debug # x86
scons mode=debug arch=x64 #64
```
  * Set or export DEBUG=1
```
set DEBUG=1 # Windows
export DEBUG=1 # Unix
```
  * Build pyv8 with setup.py
```
python setup.py build
```

_contribute by  gaussgss_

## Build with VS2010 ##
```
> set DISTUTILS_USE_SDK=true
> set MSSdk=true
> %vs2010%\vc\bin\vcvars32.bat
> python setup.py build -c msvc
```

## Build with Mac OSX 10.9 Mavericks with XCode 5 ##
XCode 5 will use libc++ as default standard C++ library by default, but Google V8 use libstdc++ by default.

You may get following error with wrong library.

```
Symbol not found: __ZSt20__throw_length_errorPKc
```

So, please set the environment variable before build V8 and PyV8

```
$ export CXXFLAGS='-std=c++11 -stdlib=libc++ -mmacosx-version-min=10.8'
$ export LDFLAGS=-lc++
$ python setup.py build
```

please check [issue #220](https://code.google.com/p/pyv8/issues/detail?id=#220) for more detail.

## FAQ ##
1. Fail to load _PyV8.so with AttributeError exception_

> If you got the exception "AttributeError: 'Boost.Python.StaticProperty' object attribute 'doc' is read-only", please check your Python version. The Python 2.6.4 introduce [a known issue](http://www.mail-archive.com/python-dev@python.org/msg42741.html) which will break boost 1.40 or earlier version. Please use Python 2.5.x/2.6.3, or upgrade your boost to 1.41 or later.