# Python

## 24 - 1. Family Trees

Define a procedure, ancestors(genealogy, person), that takes as its first input
a Dictionary in the form given above, and as its second input the name of a
person. It should return a list giving all the known ancestors of the input
person (this should be the empty list if there are none). The order of the list
does not matter and duplicates will be ignored.

```
def ancestors(genealogy, person):
```

1. 빈 list 생성
2. genealogy[person] 검색
3. 리스트에 추가 (union 이용하면 될듯)
4. 추가된 목록을 다시 genealogy에서 검색
5. 리스트에 추가
6. 모든 리스트 검토 완료 후 종료
7. 해당 리스트 출력

```
def ancestors(genealogy, person):
    queue = []
    if person in genealogy:
        queue += genealogy[person]
    for a in queue:
        if a in genealogy:
            queue += genealogy[a]
    return queue
```

일단 성공했는데 if in 구조가 두 번 반복되서 개인적으로 굉장히 불편하다.
중복되는 값을 고려하지 않은 코딩임. (근데 후손이 선조를 낳을 순 없잖아?)

```
def ancestors(genealogy, person):
    if person in genealogy:
        parents = genealogy[person]
        result = parents
        for parent in parents:
            result += ancestors(genealogy, parent)
        return result
    return []
```

기본적으로 동일한 구조다. 공부 열심히 헀구만 호호

## 24 - 2. Khayyam Triangle

Define a procedure, triangle(n), that takes a number n as its input, and
returns a list of the first n rows in the triangle. Each element of the
returned list should be a list of the numbers at the corresponding row in the
triangle.

```
def triangle(n):
```
하다가 성질남.

```
def triangle(n):
    tri = []
    for number in range(n):
        owo = []
        if number != 0:
            for chex in range(number):
                if ((chex == 0) or (chex == (number - 1))):
                   owo.append(1)
                else:
                   owo.append(tri[number - 1][chex - 1] + tri[number - 1][chex])
                tri.append(owo)
    return tri
```
아직 에러 있음. 원래 없었는데 어디서 또 생기고;  
현재 출력 시 두 레벨 아래로 출력되는 현상 발생

일단 내일 할래..