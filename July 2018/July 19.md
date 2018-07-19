# Python

## 클래스

초기자

새 객체를 생성할 때마다 실행되는 메서드. C#/C++/Java 등에서 일컫는 생성자와 약간 다르다. 파이썬에서 클래스 생성자는 실제 런타임 엔진 내부에서 실행되는데, 이 생성자 실행 도중 클래스 안에 초기자가 있는지 체크하여 만약 있으면 호출하여 객체의 변수 등을 초기화시킨다.

정적 메서드

self 파라미터를 갖지 앟고 인스턴스 변수에 엑세스할 수 없다. 객체 필드와 독립적이지만 로직상 클래스 내에 포함되는 메서드에 사용된다.

메서드 앞에 @staticmethod 라고 표시한다.

클래스 메서드

메서드 앞에 @classmethod 라고 표시한다. 정적 메서드랑 비슷하데, 객체 인스턴스를 의미하는 self 대신 cls 라는 클래스를 의미하는 파라미터를 전달받는다.

일반적으로 인스턴스 데이터를 엑세스 할 필요가 없는 경우 클래스 변수를 엑세스할 필요가 있을때 클래스 메서드를, 없을때 정적 메서드를 활용한다.

```
class Rectangle:
    count = 0 # 클래스 변수

    def __init__(self, width, height):
        self.width = width
        self.height = height
        Rectangle.count += 1

    # 인스턴스 메서드
    def calcArea(self):
        area = self.width * self.height
        return area

    # 정적 메서드
    @staticmethod
    def isSquare(rectWidth, recHeight):
        return rectWidth == rectHeight
    
    # 클래스 메서드
    @classmethod
    def printCount(cls):
        print(cls.count)

# 테스트
square = Rectangle.isSquare(5,5)
print(square) # True

rect1 = Rectangle(5, 5)
rect2 = Rectangle(2, 5)
rect1.printCount() # 2
```

그 외의 메서드

객체가 Garbage Collection 될 때 실행하는 소멸자 : __del__  
두 개의 객체 덧셈 : __add__  
두 개의 객체 뺄셈 : __sub__  
두 개의 객체 비교 : __cmp__  
문자열로 객체 표현 : __str__


객체의 생성과 사용

먼저 클래스로부터 객체를 생성한다. '객체변수명 = 클래스명()"  
만약 초기자가 있다면 해당 입력파라미터를 괄호 안에 전달한다.

```
# 객체 생성
r = Rectangle(2, 3)

# 메서드 호출
area = r.calcArea()
print("area = ", area)

# 인스턴스 변수 엑세스
r.width = 10
print("width = ", r.width)

# 클래스 변수 엑세스
print(Rectangle.count)
print(r.count)
```

위와 같이 클래스 변수 엑세스할 때 클래스명이 아닌 객체변수명을 입력하면 혼란이 올 수 있으니 하지 말자.  
파이썬에서 한 객체의 attribute에 값이 할당되면 먼저 해당 객체에 이미 동일한 attribute가 있는지 체크해서 있으면 새 값으로 치환하고, 없으면 객체에 새로운 attribute를 생성하고 값을 할당한다. 즉, r.count = 10의 경우 클래스 변수인 count를 사용하는 게 아니라 새로 그 객체에 추가된 인스턴스 변수를 사용하게 되므로 클래스 변수값은 변경되지 않는다.  
파이썬에서 한 객체의 attrivute를 읽는 순서 : 객체 내 -> 객체 소속 클래스 -> 상위 Base 클래스 -> 에러