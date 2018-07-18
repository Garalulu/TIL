# Python

## 패키지

모듈들을 모은 컬렉션.하나의 디렉토리에 놓여진 모듈들의 집합

패키지 안에 패키지 포함 가능, 사실상 파일 시스템에 비유하자면 디렉터리 개념

패키지 내 모듈을 import하려면
```
import 패키지명.모듈명
```
과 같이 쓸 수 있다.

패키지에는 __init__.py 라는 특별한 파일로 이 폴더가 패키지임을 나타낼 수 있다. __all__ 이라는 변수로 패키지 내에서 import 가능한 모듈들의 리스트를 담을 수 있다.

```
# __init__.py 내용
__all__ = ['bill']

# 패키지내 모든 모듈 import
from models.account import *
bill.charge(1, 50)
```

## 클래스

```
class MyClass:
    pass
```

pass 문은 빈 동작 혹은 아직 구현되지 않았음을 의미. 여기서는 빈 클래스

메서드

클래스 내의 함수.  
instance method : 인스턴스 변수에 엑세스할 수 있도록 객체 자신을 의미하는 "self"라는 파라미터 보유

```
class Rectangle:
    count = 0 # 클래스 변수

    # 초기자
    def __init__(self, width, height):
        # self.* : 인스턴스 변수
        self.width = width
        self.height = height
        Rectangle.count += 1
    
    # 메서드
    def calcArea(self):
        area = self.width * self.height
        return area
```
자바와 달리 인스턴스 변수 초기 선언이 없음.

클래스 변수는 메서드 밖에 존재하는 변수로서 해당 클래스를 사용하는 모두에게 공용으로 사용된다.

인스턴스 변수는 선언한 각 객체 인스턴스마다 별도로 존재한다. 

접근제한자가 없으며 기본적으로 모든 멤버가 public이다. 코딩 관례상 내부적으로만 사용하는 변수 혹은 메서드는 이름 앞에 하나의 밑줄(_)을 붙인다. (실제로는 public으로 작용)

만약 특정 변수명이나 메서드를 private으로 만들어야 한다면 두 개의 밑줄(__)을 이름 앞에 붙인다.