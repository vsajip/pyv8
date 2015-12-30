# v0.9 #
## Major Features ##
  * static link with latest v8 v2.1.2.3
  * support the v8 profiler
  * fix some critical reference count issues which may cause crash

## Minor Changes ##
  * support to use the python mapping protocol from Javascript side
  * support to setup build environment with configuration file
  * support to build as debug mode
  * support to build at Mac OS X

## Fixed Issues ##
  * [issue #17](https://code.google.com/p/pyv8/issues/detail?id=#17) handle the constructor style function call with call method
  * [issue #18](https://code.google.com/p/pyv8/issues/detail?id=#18) support python property with getter/setter
  * [issue #19](https://code.google.com/p/pyv8/issues/detail?id=#19) disable the build-in supports for python property by default, and use python side implementation
  * [issue #20](https://code.google.com/p/pyv8/issues/detail?id=#20) use BaseException.args instead of deprecated message to follow PEP 352
  * [issue #21](https://code.google.com/p/pyv8/issues/detail?id=#21) support to use the python mapping protocol from Javascript side
  * [issue #22](https://code.google.com/p/pyv8/issues/detail?id=#22) return undefined when array index out of range
  * [issue #27](https://code.google.com/p/pyv8/issues/detail?id=#27) check the environment variable V8\_HOME exists and points to a valid v8 source folder first
  * [issue #26](https://code.google.com/p/pyv8/issues/detail?id=#26) add supports for OS X 10.6 or later
  * [issue #23](https://code.google.com/p/pyv8/issues/detail?id=#23) make GCC happy
  * [issue #25](https://code.google.com/p/pyv8/issues/detail?id=#25) return value from iterator::dereference method instead of reference to a temporary object
  * [issue #26](https://code.google.com/p/pyv8/issues/detail?id=#26) rename library boost\_python\_mt to boost\_python-mt
  * [issue #29](https://code.google.com/p/pyv8/issues/detail?id=#29) add unicode method to JSError for Django
  * [issue #28](https://code.google.com/p/pyv8/issues/detail?id=#28) force convert function use string as key, and wait v8 API to provide full supports for TODO(1245389)
  * [issue #31](https://code.google.com/p/pyv8/issues/detail?id=#31) apply the patch with buildconf.py to simply setup
  * [issue #33](https://code.google.com/p/pyv8/issues/detail?id=#33) support to link with boost\_python\_mt
  * [issue #35](https://code.google.com/p/pyv8/issues/detail?id=#35) remove obsoleted v8 internal API
  * [issue #37](https://code.google.com/p/pyv8/issues/detail?id=#37) only compile AST.cpp when support Javascript AST

## Known Issues ##
  * serialize/deserialize still doesn't work
  * Javascript AST support is not complete

# v0.8 #
## Major Features ##
  * integrate with the latest v8 engine v2.0.5.2
  * both the multi-python and multi-javascript thread mode
  * the preemption shedule for multi-javascript threads
  * terminate javascript thread with JSEngine methods: terminateThread/terminateAllThread
  * the javascript extension with python or javascript
## Minor Changes ##
  * notify v8 the working status with JSEngine methods: dispose/idle/lowMemory
  * precompile javascript source with JSEngine method precompile
  * get call stack from exception with stackTrace attribute
  * set v8 flags with JSEngine method setFlags
  * build with Visual Studio 2008
  * build at MAC platform
## Fixed Issues ##
  * [issue #8](https://code.google.com/p/pyv8/issues/detail?id=#8) class instance not derived from object returned as Global causes segfault
  * [Issue #9](https://code.google.com/p/pyv8/issues/detail?id=#9) Incorrect unicode conversion between python object and javascript object on FreeBSD
  * [Issue #12](https://code.google.com/p/pyv8/issues/detail?id=#12) AttributeError: 'Boost.Python.StaticProperty' object attribute 'doc' is read-only
  * [Issue #13](https://code.google.com/p/pyv8/issues/detail?id=#13) Python fatal error during RegExp match
  * [Issue #15](https://code.google.com/p/pyv8/issues/detail?id=#15) Initialize JSArray before enter a context
  * [Issue #16](https://code.google.com/p/pyv8/issues/detail?id=#16) register multiple native JSExtensions
## Known Issues ##
  * serialize/deserialize still doesn't work :(