## Build Instructions

1. Install `clang` and `iwyu`: `sudo apt install clang-9 iwyu`
2. Configure the project: `cmake -B out/`
3. Build the project: `cmake --build out/`

## Example

```
$ cmake -B out/
-- The CXX compiler identification is GNU 9.4.0
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /modern-cmake/examples/chapter09/05-iwyu/out
$ cmake --build out/
[ 33%] Building CXX object CMakeFiles/hello.dir/main.cpp.o
Warning: include-what-you-use reported diagnostics:

/modern-cmake/examples/chapter09/05-iwyu/main.cpp should add these lines:
#include <string>    // for operator<<, string

/modern-cmake/examples/chapter09/05-iwyu/main.cpp should remove these lines:
- #include "mylib.hpp"  // lines 2-2

The full include-list for /modern-cmake/examples/chapter09/05-iwyu/main.cpp:
#include <iostream>  // for endl, basic_ostream, cout, ostream
#include <string>    // for operator<<, string
---

[ 66%] Building CXX object CMakeFiles/hello.dir/mylib.cpp.o
Warning: include-what-you-use reported diagnostics:

(/modern-cmake/examples/chapter09/05-iwyu/mylib.hpp has correct #includes/fwd-decls)

/modern-cmake/examples/chapter09/05-iwyu/mylib.cpp should add these lines:

/modern-cmake/examples/chapter09/05-iwyu/mylib.cpp should remove these lines:
- #include <vector>  // lines 2-2

The full include-list for /modern-cmake/examples/chapter09/05-iwyu/mylib.cpp:
#include "mylib.hpp"
---

[100%] Linking CXX executable hello
[100%] Built target hello
```

## Issues

- [IWYU could not find stddef.h on Ubuntu 18.04](https://github.com/include-what-you-use/include-what-you-use/issues/679#issuecomment-524034039)

## Resources

- [Original source code example from Stack Overflow](https://stackoverflow.com/a/30951493)
