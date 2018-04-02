# Unicode in Python

```python
# -*- coding: utf-8 -*-
  2
  3 def main():
  4     print "ord('A') is " + str(ord('A'))
  5
  6     """
  7     中 is considered as 3 bytes...
  8     ord only accept charactor
  9     """
 10     #print ord(b'中')
 11     #print len('中')
 12
 13     print "chr(65) is " + str(chr(65))
 14     print "unichr(25991) is " + unichr(25991)
 15
 16     x = 'ABC'
 17     xb = b'ABC'
 18     print "'ABC' is " + x
 19     print "b'ABC' is " + xb
 20
 21     asciix = 'ABC'.encode('ascii')
 22     print "'ABC'.encode('ascii') is " + asciix
 23
 24     print b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
 25     print '中文'.decode('utf8')
 26
 27     print "%s, Hello %d" % ("Peter", 100)
 28
 29 if __name__ == "__main__":
 30     main()
```

Python file format is defined in the head by `# -*- coding: utf-8 -*-`
Python print output format is `print "%s, Hello %d" % ("Peter", 100)`

Outputs:
```python
rd('A') is 65
chr(65) is A
unichr(25991) is 文
'ABC' is ABC
b'ABC' is ABC
'ABC'.encode('ascii') is ABC
中文
中文
Peter, Hello 100
```