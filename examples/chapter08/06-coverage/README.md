## Build Instructions

1. Install [lcov](https://linux.die.net/man/1/lcov): `sudo apt install lcov`
2. Configure the project: `cmake -B out/ -DCMAKE_BUILD_TYPE=Debug`
3. Build project and generate code coverage report: `cmake --build out/ -t coverage`
4. Open the coverage report in the browser: `out/coverage/index.html`

## Issues

You may get an error if there is a version mismatch between `gcov` and `g++`.

```
$ cmake --build out/ -t coverage
Capturing coverage data from .
Found gcov version: 9.4.0
Using intermediate gcov format
Scanning . for .gcda files ...
Found 3 data files in .
Processing sut.dir/rng_mt19937.cpp.gcda
/home/Modern-CMake-for-Cpp/examples/chapter08/06-coverage/out/bin/CMakeFiles/sut.dir/rng_mt19937.cpp.gcno:version 'A75*', prefer 'A94*'
geninfo: ERROR: GCOV failed for /home/Modern-CMake-for-Cpp/examples/chapter08/06-coverage/out/bin/CMakeFiles/sut.dir/rng_mt19937.cpp.gcda!
make[3]: *** [test/CMakeFiles/coverage.dir/build.make:73: test/CMakeFiles/coverage] Error 255
make[2]: *** [CMakeFiles/Makefile2:224: test/CMakeFiles/coverage.dir/all] Error 2
make[1]: *** [CMakeFiles/Makefile2:231: test/CMakeFiles/coverage.dir/rule] Error 2
make: *** [Makefile:205: coverage] Error 2
```

You can fix this problem by setting the compiler manually at the configuration step.

```
$ export CXX=/usr/bin/g++-9
$ cmake -B out/ -DCMAKE_BUILD_TYPE=Debug
```

The code coverage generation should work now: `cmake --build out/ -t coverage`
