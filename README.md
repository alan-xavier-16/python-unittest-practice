## Create a virtual environment

```shell
python -m venv .venv
```

## unittest
- unittest contains both a testing framework and a test runner. 
- A test runner is a special application designed for running tests, checking the output, and giving you tools for debugging and diagnosing tests and applications.
unittest has some important requirements for writing and executing tests.

unittest requires that:
- You put your tests into classes as methods
- You use a series of special assertion methods in the unittest.*TestCase* class instead of the built-in assert statement

Example:

```python
import unittest

class TestSum(unittest.TestCase):

    def test_sum(self):
        self.assertEqual(sum([1, 2, 3]), 6, "Should be 6")

    def test_sum_tuple(self):
        self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")

if __name__ == '__main__':
    unittest.main()
```

## How to Structure a Simple Test

Before writing tests, consider the following:

1. What do you want to test?
2. Are you writing a unit test or an integration test?

Then the structure of a test should loosely follow this workflow:

1. Create your inputs
2. Execute the code being tested, capturing the output
3. Compare the output with an expected result

For this application, you’re testing *sum()*. There are many behaviors in sum() you could check, such as:

- Can it sum a list of whole numbers (integers)?
- Can it sum a tuple or set?
- Can it sum a list of floats?
- What happens when you provide it with a bad value, such as a single integer or a string?
- What happens when one of the values is negative?

Example:

```python
import unittest

from my_sum import sum


class TestSum(unittest.TestCase):
    def test_list_int(self):
        """
        Test that it can sum a list of integers
        """
        data = [1, 2, 3]
        result = sum(data)
        self.assertEqual(result, 6)

if __name__ == '__main__':
    unittest.main()
```

## Executing Test Runners

The Python application that executes your test code, checks the assertions, and gives you test results in your console is called the **test runner**. For example, at the bottom of *test.py*, this small snippet of code:

```python
if __name__ == '__main__':
    unittest.main()
```

To execute the unittest test runner, we can use:

```shell
python test.py
```

or,

```shell
python -m unittest test
```

## More Advanced Testing Scenarios
Before you step into creating tests for your application, remember the three basic steps of every test:

1. Create your inputs
2. Execute the code, capturing the output
3. Compare the output with an expected result

It’s not always as easy as creating a static value for the input like a string or a number. Sometimes, your application will require an instance of a class or a context. What do you do then?

The data that you create as an input is known as a **fixture**. It’s common practice to create fixtures and reuse them.

If you’re running the same test and passing different values each time and expecting the same result, this is known as **parameterization**.