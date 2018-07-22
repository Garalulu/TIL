# Python

## 유닛 테스트

유닛 테스트란? 컴퓨터 프로그래밍에서 소스 코드의 특정 모듈이 의도된 대로 정확히 작동하는지 검증하는 절차다.

기본적으로 제공되는 unittest 모듈을 사용할 수 있다.

작성 방법

1. unittest 모듈 import
2. "unittest.TestCase"로부터 파생된 사용자 테스트 클래스 작성
3. 테스트 클래스 안에 "test"로 시작하는 테스트 메서드 생성. 일반적으로 테스트하고자 하는 함수나 메서드를 호출하고 그 결과값을 self.assert*() 메서드를 사용해 확인한다. (assertEqual, assertTrue, assertFalse, assertRaises, assertRegex 등 다양한 메서드 사용 가능)
4. 테스트 클래스가 완성되면 unittest.main()을 호출하여 테스트를 실행시킨다.

Example
```
# myCalc.py
def add(a, b):
    return a + b

def substract(a, b):
    return a - b
```

유닛 테스트를 위한 코드로서 unittest.TestCase로부터 파생된 MyCalcTest 클래스를 작성하였다. test_add와 test_substract 테스트 메서드를 작성하였다. 마지막 라인에 unittest.main()이 실행되면 테스트 메서드들이 실행되게 된다.

```
# tests.py
import unittest
import myCalc

class MyCalcTest(unittest.TestCase):

    def test_add(self):
        c = myCalc.add(20, 10)
        self.assertEqual(c, 30)

    def test_substract(self):
        c = myCalc.substract(20, 10)
        self.assertEqual(c, 10)

if __name__ == '__main__':
    unittest.main()
```

파이썬 unittest는 전체 스크립트 단위, 테스트 클래스 단위 또는 메서드/함수 단위로 실행할 수 있다.