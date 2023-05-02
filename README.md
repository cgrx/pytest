# Python Testing with pytest

## Cheat Sheet
| Command              | Description                                                          |
|----------------------|----------------------------------------------------------------------|
| `pytest <path>`      | Run all tests below somepath                                         |
| `pytest test_mod.py` | Run tests in a module                                                |
| `pytest test_mod.py::test_func` | Run a single test in a module                             |
| `pytest --tb=<style>` | Traceback print mode (auto/long/short/line/native/no)               |
| `pytest -q`          | Run in quiet mode                                                    |
| `pytest -v`          | Run in verbose mode                                                  |
| `pytest -vv`         | Run in more verbose mode and shows information during test failuers. |

| Method | Description |
|--------| ----------- |
| `pytest.fail()` | Explicitly fail a test |
| `pytest.raises()` | Check that an exception is raised |

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
