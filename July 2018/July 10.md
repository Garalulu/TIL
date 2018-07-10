# Python

## 27 - 1. Pick One

```
Define a procedure, pick_one, that takes three inputs: a Boolean 
and two other values. If the first input is True, it should return 
the second input. If the first input is False, it should return the third input.

For example, pick_one(True, 37, 'hello') should return 37, and
pick_one(False, 37, 'hello') should return 'hello'.
```
My Answer
```
def pick_one(check, a, b):
    if (check):
        return a
    else:
        return b
```
udacity와 같은 방식이었다. check 자체가 Boolean 형식이기 때문에 True면 a, False면 b를 출력하게 했다.

## 27 - 2. Triangular Numbers

```
The triangular numbers are the numbers 1, 3, 6, 10, 15, 21, ... They are calculated as follows.

1
1 + 2 = 3
1 + 2 + 3 = 6
1 + 2 + 3 + 4 = 10
1 + 2 + 3 + 4 + 5 = 15

Write a procedure, triangular, that takes as its input a positive integer n and returns the nth triangular number.
```
My Answer
```
def triangular(number):
    if number == 1:
        return 1
    return number + triangular(number-1)
```
Udacity
```
def triangular(n):
    number = 0
    for i in range(1, n+1):
        number = number + i
    return number
```
재귀문과 반복문 차이

## 27 - 3. Linear Time

```
For the procedures below, check the procedures whose running time scales linearly with the length of the input in the worst case. You may assume the elements in input_list are fairly small numbers.
```

```
1.
def proc1(input_list):
    maximum = None
    for element in input_list :
        if not maximum or maximum < element:
            maximum = element
    return maximum

2.
def proc2(input_list):
    sum = 0
    while len(input_list) > 0:
        sum = sum + input_list[0]   # Assume input_list[0] is constant time
        input_list = input_list[1:]  # Assume input_list[1:] is constant time
    return sum

3.
def proc3(input_list):
    for i in range(0, len(input_list)):
        for j in range(0, len(input_list)):
            if input_list[i] == input_list[j] and i != j:
                return False
    return True
```
답은 1, 2번.

1번  
반복문을 반복하는데 동일한 시간이 소요된다.

2번
1번과 마찬가지

3번
input_list를 두번 이용하므로 제곱의 시간이 든다.