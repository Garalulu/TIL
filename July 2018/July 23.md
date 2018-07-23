# Python

## 유닛 테스트

Test Fixture

테스트 시나리오에 따라 어떤 경우는 테스트 전에 사전 준비 작업을 할 필요가 있다. 또 테스트가 끝난 후 Clean up을 해야 하는 경우도 있을 수 있다.  
unittest는 사전 준비 작업을 위해 setUp()이라는 메서드를, 사후 Clean up 처리를 위해 tearDown()이라는 메서드를 사용할 수 있도록 되어있다.

```
# myUtil.py
import os

def filelen(filename):
    f = open(filename, "r")
    f.seek(0, os.SEEK_END)
    return f.tell()

def count_in_file(filename, char_to_find):
    count = 0
    f = open(filename, "r")
    for word in f:
        for char in word:
            if char == char_to_find:
                count += 1
    return count
```

```
import unittest
import os
import myUtil

class MyUtilTest(unittest.Testcase):
    testfile = 'test.txt'

    # Fixture
    def setUp(self):
        f = open(MyUtilTest.testfile, 'w')
        f.write('1234567890')
        f.close()

    def tearDown(self):
        try:
            os.remove(MyUtilTest.testfile)
        except:
            pass
    
    def test_filelen(self):
        leng = myUtil.filelen(MyUtilTest.testfile)
        self.assertEqual(leng, 10)

    def test_count_in_file(self):
        cnt = myUtil.count_in_file(MyUtilTest.testfile, '0')
        self.assertEqual(cnt, 1)

if __name__ == '__main__':
    unittest.main()
```

이후 Python Comprehension부터는 아직 몰라도 될듯