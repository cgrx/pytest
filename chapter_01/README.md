# Getting Started with pytest

## Test Discovery
1. Test discovery is the part of pytest execution where pytest goes off and finds which tests to run.
2. Convention :
    - Test files should be named `test_<something>.py` or `<something>_test.py`. 
    - Test methods and functions should be named `test_<something>`.
    - Test classes should be named `Test<Something>`.
3. Test discovery is recursive. It will find all the tests in the current directory and all subdirectories.
4. Test discovery is configurable. You can tell pytest to ignore certain directories or files, or to only look at certain directories or files.

## Test Outcomes
| Test Outcome | Meaning |
|--------------|---------|
| PASSED (.) | The test ran successfully |
| FAILED (F) | The test did not run successfully |
| SKIPPED (s) | The test was skipped |
| XFAIL (x) | The test was not supposed to pass, and it ran and failed. |
| XPASS (X) | The test was marked with xfail, but it ran and passed. |
| ERROR (E) | An exception happened during the test execution. |
