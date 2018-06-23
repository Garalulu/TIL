# Python

Q&A time
- so this is a good question.

## 25 - 1. Pythonic

1. what does it mean to be pythonic?

이 강의에서는 되도록 python의 다양한 기능을 이용?해서 진행하기보단 학생들이 현명한 방법을 찾아 스스로 진행하길 바란다.

## 25 - 2. Python Versions

2. Python 3가 이미 출시되었는데 왜 2를 배우나요? 구 버전이라 실생활에 별로 도움이 되지 않을 것 같아요.

우리가 배운 내용은 어떤 언어를 사용하든 상관없고, 그 개념을 배운 것이다. 아직 Python 2는 많이 쓰이고, 쉽게 3로 전환 가능하다.

## 25 - 3. Using Recursion

3. when do you use a recursive definition versus a 'while' loop?

while을 쓰거나 재귀문을 쓰는건 동일하지만, 불필요한 procedure의 호출을 할 필요 없는 while문을 보통 많이 쓴다. 가끔은 재귀문을 쓰는게 훨씬 간단하고 멋진 해결책이 될 수 있다.

## 25 - 4. Recursion in Other Languages

4. I always though resursive calls were more efficient that iterative functions.

Python은 새로운 procedure를 호출할 때 stack frame이 필요하고, 재귀문에서 이를 반복하면 상당히 많은 메모리가 소모된다. 다른 언어에서는 이를 방지하는 해결책이 있지만 Python에는 없기 때문에 iterative func을 권장한다. 우리가 재귀문을 배우는 이유는 새로운 생각법을 가지기 위함이고, 프로그래밍을 할 때 다양한 사고를 기르기 좋기 때문이다.

## 25 - 5. Pagerank

5. PageRank 알고리즘의 복잡성과 Google 또는 다른 검색엔진과 연관성

우리가 만든 PageRank는 이전에 Google이 사용했던 알고리즘에 가깝다. AltaVista에서 나타난 검색어 중복 문제처럼 여러 이슈가 생겨나면서 요즘 엔진에서는 더 복잡해진다.
