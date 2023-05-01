# Getting Started with pytest

## Setup
1. Create local directory
```shell
mkdir .venv
```
2. Activate virtual environment
```shell
pipenv shell
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

tests/test_one.py .                                                                                                                                                                                                          [100%]
================================================== 1 passed in 0.01s ==================================================
```
