## Build Instructions

1. Install [lcov](https://linux.die.net/man/1/lcov): `sudo apt install lcov`
2. Configure the project: `cmake -B out/ -DCMAKE_BUILD_TYPE=Debug`
3. Build project and generate code coverage report: `cmake --build out/ -t coverage`
4. Open the coverage report in the browser: `out/coverage/index.html`
