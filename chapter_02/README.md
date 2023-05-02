# Writing Test Functions

## Knowledge Building Tests
1. When we stumble upon a new data-structure, we should write tests to understand how it works. These suits of tests are called knowledge building tests.
2. The objective of these tests are not to test the correctness of the code, but to understand how the data-structure works.
   - We are not interested in the edge or corner cases.
   - We are not interested in performance issues.
   - We are only interested to check how the data-structure works, and use this oppurtunity to document it for future users.

## Using `assert` Statements
1. `assert` statements are used to check for conditions that should always be true/ should never occur.
2. When an `assert` statement fails, it throws an `AssertionError` exception.
3. `pytest` intercepts the `AssertionError` exception and reports it as a test failure. Additionally, it uses `assert rewriting` to make the error messages more informative.
4. To get more information about `AssertionError` exceptions, use `-vv` option with `pytest`.
5. In cases where we can't use `assert` statements, we can use `pytest.fail()` to raise an exception and fail the test. However, we won't get the benefit of `assert rewriting` in this case.

## Using `pytest.raises` Context Manager
1. In TDD, we have the concept of expected failures (i.e.) code should raise an exception in certain cases.
   - If a different exception is raised, the test should fail.
   - If no exception is raised, the test should fail.
2. `pytest.raises` context manager is used to check for exceptions in such cases.
3. We can pass regex to the context manager to check the exception message.

## Structuring Tests
1. Tests should be structured in a way that it is easy to understand the test suite, and isolate failures.
2. We use the following structure for tests (AAA):
   - (Given) Arrange: Create the objects and set up the conditions for the test.
   - (When) Act: Perform the action that we want to test.
   - (Then) Assert: Check that the result is as expected.
3. The structure helps to keep test functions organized and focused on testing one behavior.
4. A common anti-pattern is to have multiple AAA in a single test function. This makes it difficult to understand the test function, and isolate failures.
5. If we have multiple closely related test functions, we can group then to a test class. This helps to keep the test functions organized, and share common setup code. However, avoid using inheritance in test classes as it will hinder readability.
