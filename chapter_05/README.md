# Parametrization

1. To turn one test function into many test cases, we can use parametrization. This is necessary for through testing.
   - Parametrized testing refers to adding parameters to our test functions.
   - Passing in multiple sets of arguments to the test to create new test cases.
2. Ways to implement parameterized testing
   - Parametrizing functions
   - Parametrizing fixtures
   - Using a hook function called pytest_generate_tests
3. Parametrizing functions :
   - We can parametrize a test function by using the `pytest.mark.parametrize` decorator.
   - The decorator takes two arguments: a list of names of the parameters and the list of values to be passed to the test function.
   - The test function will be called once for each set of parameters.
   - In case of multiple parameters, pytest will display the test function name with the parameters (hyphen delimited) in parentheses.
4. Parametrizing fixtures :
   - We can move the parameter list to a fixture. This is done using the `pytest.fixture` decorator with list of parameters as an argument to `params` keyword argument.
   - Every time a test dependent of the fixture is run, it is run for each set of parameters.
   - The advantage here is that :
     + We can have set-up, and tear-down code for each set of parameters in the fixture function.
     + Same set of parameters can be used by multiple functions.
   - A good thumb-rule : Parametrize function if you want same test, but different data. Parametrize fixture if you want same test, but different start state.
5. Using a hook function called pytest_generate_tests :
   - We create a `pytest_generate_tests` hook function with metafunc as an argument.
   - We can use the `metafunc.parametrize` method to parametrize the test function.
     + The method takes two arguments: a list of names of the parameters and the list of values to be passed to the test function.
     + We can parametrize multiple parameters in the same `metafunc.parametrize` call.
   - Advantages :
     + Using `metafunc.config.getoption("--<someflag>")` we can parametrize the test function based on the command line options.
     + We can parametrize a parameter based on the value of another parameter being requested. For example : Value returned if `parameter_a` is requested alone can be different from value returned if `parameter_a` and `parameter_b` are requested together.
