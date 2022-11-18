# aws-c-s3-testcoverage

Test coverage based on aws-c-s3.

Page can be found [https://tingdaok.github.io/aws-c-s3-testcoverage/test](https://tingdaok.github.io/aws-c-s3-testcoverage/test).

Used gcov and [gcovr](https://gcovr.com/en/stable/) to create the HTML page.

## Steps to generate the test coverage report:

- build your cmake project with `"CMAKE_C_FLAGS": "-fprofile-arcs -ftest-coverage"`
- in your build folder, run `ctest`
- after tests finish, run `ctest -T coverage`
- The *.gcovr files will be in your build/Testing/CoverageInfo/ folder

## Generate visualized HTML page:

- Install gcovr
- put the following as `./gcovr.cfg`:

```
filter = /aws-c-s3/        # your source code dir
filter = /install/include/ # your install dir
html-details = yes  # info about each source file
output = ./report/test.html
```

- `gcovr -k -g -e tests/ -v ./build/Testing/CoverageInfo/`
- details can be found [gcovr](https://gcovr.com/en/stable/)
