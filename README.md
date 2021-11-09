## Create a virtual environment

```bash
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