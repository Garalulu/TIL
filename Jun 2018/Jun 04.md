# Python

## 23 - 1. Recursive Grammars

Word -> udacity
Word -> a Word

-> Word로 시작할 경우 a Word로 인해 무한 단어 생성 가능

Word -> Pre udacious
Pre -> super
Pre -> Pre super

-> Pre super로 인해 무한 단어 생성 가능

Word -> Root Tail
Root -> uda
Root -> boda
Root -> Tail
Tail -> cious
Tail -> city

-> 추가적으로 늘어날 만한 연결고리가 없어서 불가능

## 23 - 2. Rabbits Multiplying

```
def rabbits(n):
    if (n == 2 or n == 1):
        return 1
    elif (n <= 5):
        return rabbits(n-1) + rabbits(n-2)
    else:
        return rabbits(n-1) + rabbits(n-2) - rabbits(n-5)
```

5개월 후부터 점점 죽어가는 토끼 가족들

## 23 - 3. Spreading Udaciousness

```
def hexes_to_udaciousness(n, spread, target):
    if (n >= target):
        return 0
    else:
        return 1 + hexes_to_udaciousness(n + n * spread, spread, target - n)
```
n * spread가 아니라  
n + n * spread였다고 한다

## 23 - 4. Deep Count
```
# For this procedure, you will need a way to test if a value is a list. We have
# provided a procedure, is_list(p) that does this:

def is_list(p):
    return isinstance(p, list)

# It is not necessary to understand how is_list works. It returns True if the
# input is a List, and returns False otherwise.

def deep_count(p):
    sum = 0
    for owo in p: 
        sum = sum + 1
        if is_list(owo):
            sum = sum + deep_count(owo)
    return sum
```

아니 그냥 무조건 1씩 더하면서 한다니..  
나는 리스트면 재귀하고 아니면 1 더하고 했는데 도통 되지 않았음.  
보니까 껍질도 새는 거 같던데, 그래서 그냥 안에 sum = sum + 1을 넣은듯

# Summary

검색엔진 어렵다  
단순 재귀 함수 구조를 알기 위해서는 먼저 길고 긴 주석을 해석하는 능력을 기르자