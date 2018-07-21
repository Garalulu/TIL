# Python

## 클래스

클래스 상속과 다형성

클래스를 상속받기 위해서는 자식 클래스에서 클래스명 뒤에 부모 클래스 이름을 괄호와 함께 넣으면 된다.

```
class Animal:
    def __init__(self, name):
        self.name = name
    def move(self):
        print("move")
    def speak(self):
        pass

class Dog (Animal):
    def speak(self):
        print("bark")

clas Duck (Animal):
    def speak(self):
        print("quack")
```

자식 클래스는 부모 클래스의 멤버를 호출하거나 사용할 수 있다.

다형성도 지원하기 때문에 객체의 타입에 따라 서로 다른 메서드가 호출될 수 있다.

## 예외처리

```
try:
    문장1
    문장2
except:
    예외처리
finally:
    마지막에 항상 수행
```

except 뒤에 아무것도 붙이지 않으면 어떤 에러가 나오든간에 수행한다.

복수의 Exception들이 동일한 수행 처리를 한다면 하나의 except 문에 묶어 쓸 수 있다.

발생된 exception을 무시하기 위해서는 pass문을 사용한다. 개발자가 에러를 던지기 위해서는 raise문을 사용한다.

```
# pass
try:
    check()
except FileExistsError:
    pass

# raise
if total < 0:
    raise Exception('Total Error')