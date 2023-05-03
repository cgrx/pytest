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
5. The fixture and test function are separate functions. Carefully naming your fixtures to reflect the work being done in the fixture or the object returned from the fixture, or both, will help with readability.

## Setup and Teardown
1. Setup and teardown are the two phases of a test.
2. Setup is the phase where the system under test is initialized.
3. Teardown is the phase where the system under test is cleaned up.
4. We can use the `@pytest.fixture` decorator to create fixtures that run setup and teardown code.
5. To run teardown code, we can use the `yield` keyword in the fixture function
   - The code after the `yield` keyword is the teardown code.
   - The code before the `yield` keyword is the setup code.
   - The code after the `yield` keyword is executed after the test function completes regardless of whether
     the test function passed or failed.

## Fixture Scope
1. The scope of a fixture determines how often the setup, and teardown code is run. This becomes important
   when we have multiple tests that depend on the same fixture.
2. Scopes :
   - `function` : The default scope. The fixture is run once for each test function that depends on it.
   - `class` : The fixture is run once for each test class that depends on it.
   - `module` : The fixture is run once for each module that depends on it.
   - `package` : The fixture is run once for each package that depends on it.
   - `session` : The fixture is run once for the entire test session.
3. We can specify the scope of a fixture by passing the `scope` argument to the `@pytest.fixture` decorator.

## Sharing Fixtures
1. When there are multiple tests sharing a fixture, they need not be located in the same module.
2. To share fixtures among multiples test files, we can use `conftest.py` file. The fixtures defined in `conftest.py` are available to all the tests in the directory and its subdirectories.
3. The `conftest.py` file is a plugin that is automatically discovered by pytest.
4. As the `conftest.py` file is a plugin, it can also contain hooks and other pytest related code. However, should not be imported by the test files.

## Multiple Level Fixtures
1. When we have fixtures that are shared, we can run into the problem of side-effects (i.e) tests change state of fixtures, and the changes are visible to other tests.
2. The side-effects break the thumb-rule of tests being independent of each other.
3. To avoid side-effects, we need to use multi-level fixtures. For example :
   - An expensive database connection is opened at the session level.
   - The database connection is passed as a parameter to a fixture that runs at the function level.
   - The function scope fixtures, clears the state of the database connection before passing it to the test
     function.
   - The test function uses the database connection to run the test.
4. In some alternative scenarios, we need a populated DB connection for multiple tests. In such cases :
   - We have a session level fixture that establishes connection.
   - We have a session level fixture with records that will populate a DB.
   - We have a function level fixture that populates the DB with the records from the session level fixture before each test.
5. Using multiple stage fixtures like this can provide some incredible speed benefits and maintain test order independence.
