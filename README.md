# Python Testing with pytest

## Index
| Chapter                            | Description                                                                                                  |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Chapter 1](chapter_01/README.md)  | • Getting Started with pytest<br> • Test Discovery<br> • Test Outcomes                                       |
| [Chapter 2](chapter_02/README.md)  | • Knowledge building tests<br> • Assert statements<br> • Expected failures<br> • Structuring tests           |
| [Chapter 3](chapter_03/README.md)  | • Fixtures<br> • Setup and Teardown<br> • Fixture Scope<br> • Sharing Fixtures<br> • Multiple Level Fixtures |
| [Chapter 4](chapter_04/README.md)  | • `monkeypatch`                                                                                              |
| [Chapter 5](chapter_05/README.md)  | • Parametrizing Functions<br> • Parametrizing Fixtures<br> • `pytest_generate_tests`                         |

## Cheat Sheet
| Command                         | Description                                                             |
|---------------------------------|-------------------------------------------------------------------------|
| `pytest <path>`                 | Run all tests below some path                                           |
| `pytest test_mod.py`            | Run tests in a module                                                   |
| `pytest test_mod.py::test_func` | Run a single test in a module                                           |
| `pytest --tb=<style>`           | Traceback print mode (auto/long/short/line/native/no)                   |
| `pytest -q`                     | Run in quiet mode                                                       |
| `pytest -v`                     | Run in verbose mode                                                     |
| `pytest -vv`                    | Run in more verbose mode and shows information during test failuers.    |
| `pytest -s`                     | Shortcut for `--capture=no`. Turns off output capture for passed tests. |
| `pytest --setup-show`           | Shows the order of operations of tests and fixtures                     |
| `pytest --fixtures`             | Show available fixtures under `PWD`                                     |
| `pytest --fixtures-per-test`    | Show available fixtures for a test                                      |
| `pytest --basetemp=mydir`       | Change the base temporary directory for test execution.                 |

| Method                            | Description                                                              |
|-----------------------------------|--------------------------------------------------------------------------|
| `pytest.fail()`                   | Explicitly fail a test                                                   |
| `pytest.raises()`                 | Check that an exception is raised                                        |
| `pytest.fixture(name=<name>)`     | Rename fixtures                                                          |
| `@pytest.fixture(autouse=True)`   | Run a fixture for all tests without being named by test/ another fixture |
| `@pytest.fixture(scope=<scope>)`  | Set the scope of a fixture                                               |

| Fixture            | Description                                                                                             |
|--------------------|---------------------------------------------------------------------------------------------------------|
| `tmp_path`         | Function-scope fixture returns a `pathlib.Path` instance that points to a temporary directory           |
| `tmp_path_factory` | Session-scope fixture returns a TempPathFactory object. Use `mktemp()` to create temporary directories  |
| ` capsys`          | Temporarily disable normal output capture from pytest                                                   |
| `capfd`            | Capture output from file descriptors 1 and 2                                                            |
| `capsysbinary`     | Capture binary output                                                                                   |
| `capfdbinary`      | Capture binary output from file descriptors 1 and 2                                                     |
| `caplog`           | Capture log output                                                                                      |
| `monkeypatch`      | Dynamically modify classes or modules during runtime                                                    |
| `cache`            | Used to store and retrive values across test runs                                                       |
| `pytestconfig`     | Access to configuration values, plugin manager, and plugin values                                       |

## Setup
1. Create local directory
```shell
mkdir .venv
```
2. Create and activate virtual environment
```shell
pipenv install
source .venv/bin/activate
```
3. Install dependencies
```shell
pipenv sync
```
4. Run tests
```shell
pytest tests/
================================================== test session starts ================================================
platform linux -- Python 3.10.6, pytest-7.3.1, pluggy-1.0.0
rootdir: /media/ganeshranganath/Data/pytest/chapter_01
collected 1 item

tests/test_one.py .                                                                                              [100%]
================================================== 1 passed in 0.01s ==================================================
```
