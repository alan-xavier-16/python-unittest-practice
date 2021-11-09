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
- You use a series of special assertion methods in the unittest._TestCase_ class instead of the built-in assert statement

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
