
# Lab

Continuous testing

## Objectives

- Learn how to write and run unit tests for your functions
- Use test-driven development (TDD)

## Before starting

1. Read [00.lab-essentials](../00.lab-essentials) to see if you need to install anything.
2. Create and activate virtual environment: `env_mlops`
3. In this virtual environment install `pytest`: `pip install pytest`
4. Go to the [pytest doc](https://docs.pytest.org/en/7.0.x/getting-started.html). Read how the files and test functions should be named, so pytest can discover them automatically.

## Prepare the environment

During testing you will write python functions and the tests that will test those functions. For this to work, files with tests need to be named correctly to be recognized by pytest, and also functions need to be in the correct place to be found by Python. The organisation and configuration of the project is important. 

Below are two ways how this can be done. Both examples are based on the example from [Create your first test](https://docs.pytest.org/en/7.0.x/getting-started.html#create-your-first-test).

NOTE: If running `pytest` doesn't work, try running `python -m pytest` instead.

### Fuctions and tests in the same file

1. Create a folder `unit_testing_simple`.
2. In the folder create a file `test_sample.py`.
3. Copy the example code from the website to the file:

```python
def func(x):
    return x + 1

def test_answer():
    assert func(3) == 5
```

4. In the terminal that you used to create and activate your virtual environment (e.g. Anaconda Power Shell or Anaconda Prompt) go to the folder `unit_testing_simple`.
5. Run `ls` (or `dir`) to list all the files in the folder. You should see the `test_sample.py`. Thah's how you know if you are in the right place.
6. Run `pytest`. The output should look like this:

```
================================================================= test session starts ==================================================================
platform linux -- Python 3.9.12, pytest-7.2.0, pluggy-1.0.0
rootdir: /home/adaltas/Documents/teaching_tests/unit_testing/unit_testing_simple
collected 1 item                                                                                                                                       

test_sample.py F                                                                                                                                 [100%]

======================================================================= FAILURES =======================================================================
_____________________________________________________________________ test_answer ______________________________________________________________________

>   ???
E   assert 4 == 5
E    +  where 4 = func(3)

/home/adaltas/Documents/teaching_tests/unit_testing_simple/test_sample.py:7: AssertionError
=============================================================== short test summary info ================================================================
FAILED test_sample.py::test_answer - assert 4 == 5
================================================================== 1 failed in 0.01s ===================================================================
```

7. Try to understand what it means. Help yourself with the documentation.

### Fuctions and tests are separated

Having the functions and the tests in the same file is not a good practice. It works well for short learning examples, but it leads to unreadable projects in real life.
Therefore, we need to split the functions and the tests to separate files to properly organize a project.

1. Create a folder `unit_testing_best_practice`.
2. Inside, create two subfolders on the same level: `src`, `test`. All the functions will be saved to the `src` folder and all the tests to `test` folder.
3. In `src`, create a file `sample.py`. 
4. Inside, copy the function `func` from [Create your first test](https://docs.pytest.org/en/7.0.x/getting-started.html#create-your-first-test).

```python
def func(x):
    return x + 1
```

5. In `test`, create a file `test_sample.py`.
6. Inside, copy the test `test_answer` from [Create your first test](https://docs.pytest.org/en/7.0.x/getting-started.html#create-your-first-test).

```python
def test_answer():
    assert func(3) == 5
```

7. Since we have two folders now, from which location will we run `pytest`? Why?
8. Pytest will always be run from the `unit_testing_best_practice/test`. To execute correctly, we need to include two information to `test_sample.py`:
	- import the module with our functions
	- point to the module location (do you know the difference between the absolute and relative path?)

Now the `test_sample.py` should look like this:

```python
import sys
# Always run from unit_testing_best_practice/test
sys.path += ['../src'] 

from sample import *

def test_answer():
    assert func(3) == 5
```

9. In the terminal, go to the `unit_testing_best_practice/test`.
10. Run `pytest`. The output should be the same as before.
11. Do you need to fix the function or the test to make the test pass (and the function to be correct)?

## Unit testing

Imagine you are developing an application, where users need to register. They need to fill in their username, email and password.

Your job is to write the functions that will accept those parameters from the user input (in command line) and test if they follow the criteria:

- user name:
  - not empty
  - no spaces
- password:
  - at least 8 characters
  - at least one number
  - at least one letter
  - at least one special character
- email:
  - contains `@` and `.`

Run tests by running `pytest` in the terminal. 

If you finished, you can check out [what else you can do with pytest](https://towardsdatascience.com/pytest-with-marking-mocking-and-fixtures-in-10-minutes-678d7ccd2f70).

## Test-driven development (TDD)

Develop a function that will test if the input si a prime number. Use TDD to do that. Follow [this tutorial](https://stackabuse.com/test-driven-development-with-pytest/) if you need help.

## Test coverage

How to know if you wrote enough tests or not: https://medium.com/@sumanrbt1997/code-coverage-with-pytest-1f72653b0bf2

## Troubleshooting

If you have problems running your tests:

1. Check that you read the tutorial correctly and that you reall followed the instruction.
2. Copy your error to browser (or describe it properly) and Google it. Since pytest is much used by the Python community, you have a big chance that somebody else already resolved the same issue.
3. When you open a link with a potential solution, don't just scroll through the page, but read. (Even if you don't understand it. You have to start somewhere.)
4. Try out the proposed solution.    
