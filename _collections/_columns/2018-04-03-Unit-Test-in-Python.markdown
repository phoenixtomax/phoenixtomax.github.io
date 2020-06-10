---
layout: default 
title:  "Python Unit Test"
author: Skipper
date:   2018-04-03 00:00:00 +0200
image: http://www.scrollpublishing.com/store/media/Thomas-Payne.jpg
---
# Python Unit Test

##Basic Unit Test

Test Class
```python
  1 class Widget:
  2     name_ = "Default"
  3     size_ = set([0, 0])
  4
  5     def __init__(self, name):
  6         self.name_ = name
  7
  8     def size(self):
  9         return self.size_
 10
 11     def resize(self, height, width):
 12         self.size_ = ([height, width])
 13
 14     def dispose(self):
 15         self.name_ = "Default"
 16         self.size_ = None
```
Test Case
```python
  1 import unittest
  2
  3
  4 class MyTestCase(unittest.TestCase):
  5
  6     def test_upper(self):
  7         self.assertEqual('foo'.upper(), 'FOO')
  8
  9     def test_isupper(self):
 10         self.assertTrue('FOO'.isupper())
 11         self.assertFalse('Foo'.isupper())
 12
 13     def test_split(self):
 14         s = 'hello world'
 15         self.assertEqual(s.split(), ['hello', 'world'])
 16
 17         with self.assertRaises(TypeError): # Exception
 18             s.split(2)                     # It should be exception here
 19
 20 if __name__ == '__main__':
 21     # unittest.main()
 22
 23     suite = unittest.TestLoader().loadTestsFromTestCase(MyTestCase)
 24     unittest.TextTestRunner(verbosity=2).run(suite)
```

## Advanced Unit Test
```python
  1 import unittest
  2 import sys
  3 import Widget
  4
  5 class WidgetTestCase(unittest.TestCase):
  6     @classmethod
  7     def setUpClass(cls):
  8         pass
  9
 10     @classmethod
 11     def tearDownClass(cls):
 12         pass
 13
 14     def setUp(self):
 15         self.widget = Widget.Widget("The widget")
 16
 17     def tearDown(self):
 18         self.widget.dispose()
 19         self.widget = None
 20
 21     def test_default_size(self):
 22         self.assertEqual(self.widget.size(), ([50, 50]),
 23                          'incorrect default size')
 24
 25     def test_resize(self):
 26         self.widget.resize(100, 150)
 27         self.assertEqual(self.widget.size(), ([100, 150]),
 28                          'wrong size after resize')
 29
 30     @unittest.skip("demostrating skipping")
 31     def test_nothing(self):
 32         pass
 33
 34     @unittest.skipUnless(sys.platform.startswith("win"), "requires Windows")
 35     def test_windows_support(self):
 36         # windows specific testing code
 37         pass
 38
 39     @unittest.expectedFailure
 40     def test_fail(self):
 41         self.assertEqual(1, 0, "broken")
 42
 43 if __name__ == '__main__':
 44
 45     """ No.1 Method """
 46     """
 47     widgetTestSuite = unittest.TestSuite()
 48     defaultSizeTestCase = WidgetTestCase('test_default_size')
 49     resizeTestCase = WidgetTestCase('test_resize')
 50
 51     widgetTestSuite.addTest(defaultSizeTestCase)
 52     widgetTestSuite.addTest(resizeTestCase)
 53     """
 54
 55     """ No.2 Method """
 56     widgetTestSuite = unittest.TestLoader().loadTestsFromTestCase(WidgetTestCase)
 57
 58     unittest.TextTestRunner(verbosity=2).run(widgetTestSuite)
 59     # unittest.main()
```