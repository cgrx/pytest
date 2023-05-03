# pytest Fixtures

## Introduction
1. Fixtures are helper functions that run before (sometimes after) each test function to which they are
   applied.
2. Typically, we use fixtures to initialize objects/environment that are used by the system under test.
3. Fixtures are created using the `@pytest.fixture` decorator.
    - When a function is decorated with `@pytest.fixture`, pytest will run the function before each test
      that depends on it.
    - The test function will receive the fixture object as an argument.
    - The object returned by the fixture function is available to the test function via the fixture namesake
      argument.
4. Exceptions are handled differently when raised from a fixture function.
    - If the exception is raised before the fixture function returns, it results in an "Error".
    - If the exception is raised after the fixture function returns (i.e.) from test function, it results in
      a "Failure".

## Setup and Teardown
## Tracing Fixture Execution
## Fixture Scope
## Sharing Fixtures
## Finding Fixtures
## Multiple Level Fixtures
## Multiple Fixtures per Test or Fixture
## Dynamic Fixture Scope
## `autouse` Fixtures
## Renaming Fixtures
