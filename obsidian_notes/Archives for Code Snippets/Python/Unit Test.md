---
tags:
  - code
  - code_snippet
  - python/unit_test
keywords: 
topics: 
language: Python
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Use `unittest` package to do unit testing



## Code


```python
import unittest

class TestStringMethods(unittest.TestCase):

    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())
        self.assertFalse('Foo'.isupper())

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):
            s.split(2)

if __name__ == '__main__':
    unittest.main()
```





-----------
##  Recommended Notes

-  [`unittest`](https://docs.python.org/3/library/unittest.html#module-unittest "unittest: Unit testing framework for Python.") — Unit testing framework