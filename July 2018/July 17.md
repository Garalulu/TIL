# Python

## 함수

```
def 함수명(입력파라미터):
    문장1
    문장2
    [return 리턴값]
```

1. 파라미터 전달방식

Pass by Assignment : 호출자가 입력 파라미터 객체에 대해 레퍼런스를 생성하여 레퍼런스 값을 복사하여 전달한다.

immutable : 함수 외부에서 변하지 않음  
mutable : 함수 외부에서 변함(반영됨)

default parameter : 호출자가 전달되지 않으면 디폴트로 지정된 값 사용

```
def calc(i, j, factor = 1):
    return i * j * factor

result = calc(10, 20)
print(result)
```

factor에 값을 받지 않아서 디폴트로 지정된 1 할당

named parameter : 함수 정의 순서가 아닌 임의 순서로 파라미터 전달

```
def report(name, age, score):
    print(name, score)

report(age = 10, name = "Kim", score = 80)
```

가변길이 파라미터 : 함수의 입력파라미터 갯수 임의화

```
def total(*numbers):
    tot = 0
    for n in numbers:
        tot += n
    return tot

t = total(1,2)
print(t)
t = total(1,5,2,6)
print(t)
```

## Module

코드를 논리적으로 묶어서 관리하고 사용할 수 있도록 하는 것

함수, 클래스 혹은 변수가 정의될 수 있으며 실행 코드 포함 가능


표준 라이브러리 모듈을 제공하니 참고
```
import math
n = math.factorial(5)
```

하나의 모듈에서 하나의 함수만 빼서 import 가능

```
from math import factorial

n = factorial(5) / factorial(3)
```

from... import(함수1, 함수2) 가능

from을 쓴 경우에는 모듈명 없이 직접 함수명 사용

함수명을 임의로 바꿀 수 있음  
from ... import 함수 as Alias

모듈을 스크립트로 실행할 때는 __name__가 __main__이 되며, import하여 사용할 때는 해당 파일의 이름이 된다.
