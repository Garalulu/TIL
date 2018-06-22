# Python

## 24 - 2. Khayyam Triangle

Double Gold Star
```
def triangle(n):
    output = []
    for count in range(n):
        sub_out = []
        for number in range(count + 1):
            if (number == 0 or number == count):
                sub_out.append(1)
            else:
                sub_out.append(output[count - 1][number - 1] + output[count - 1][number])
        output.append(sub_out)
    return output
```
머리를 비우고 음악 들으면서 하니 잘됨. 깔ㅡ끔  
저번에 했을땐 반복문에서 range가 0~(n-1)까지 작용하는 거를 고려하지 않고 먼저 짠 뒤 만들었기 때문에 헷갈렸다.   
이번엔 먼저 +1 하고 시작.  
막상 해보니 너무 단순하네; 어제 제정신 아니었는듯

// udacity answer
```
def make_next_row(row):
    result = []
    prev = 0
    for e in row:
        reult.append(e + prev)
        prev = e
    result.append(prev)
    return result

def triangle(n):
    result = []
    current = [1]
    for unused in range(0, n):
        result.append(current)
        current = make_next_row(current)

    return result
```
오 함수 두개를 쓸 생각은 안해봤는데 훨씬 깔끔하긴 한듯.  
나는 피라미드 양 쪽 끝이 1이라고 가정해놓고 차곡차곡 쌓여진 위 피라미드 값을 가져왔는데 요건 위 피라미드 값을 가져와서 두개씩 차곡차곡 더하는 형식

.. 내가 쓴 코드가 더 짧다는걸로 만족하고 넘어가도록 하자

## 24 - 3. Only a Little Lucky

Triple Gold Star

```
The idea of quicksort is quite simple:

If the list has zero or one elements, it is already sorted.

Otherwise, pick a pivot element, and split the list into two partitions: one contains all the elements equal to or lower than the value of the pivot
element, and the other contains all the elements that are greater than the
pivot element. Recursively sort each of the sub-lists, and then return the
result of concatenating the sorted left sub-list, the pivot element, and the
sorted right sub-list.

For simplicity, use the first element in the list as your pivot element (this
is not usually a good choice, since it means if the input list is already
nearly sorted, the actual work will be much worse than expected).

def ordered_search(index, ranks, keyword):

#print ordered_search(index, ranks, 'Hummus')
#>>> ['http://udacity.com/cs101x/urank/kathleen.html',
#    'http://udacity.com/cs101x/urank/nickel.html',
#    'http://udacity.com/cs101x/urank/arsenic.html',
#    'http://udacity.com/cs101x/urank/hummus.html',
#    'http://udacity.com/cs101x/urank/index.html']

#print ordered_search(index, ranks, 'the')
#>>> ['http://udacity.com/cs101x/urank/nickel.html',
#    'http://udacity.com/cs101x/urank/arsenic.html',
#    'http://udacity.com/cs101x/urank/hummus.html',
#    'http://udacity.com/cs101x/urank/index.html']


#print ordered_search(index, ranks, 'babaganoush')
#>>> None
```
갈수록 태산이네

저는 답을 보겠습니다 ㅎㅎ

udacity answer
```
def quicksort_pages(pages, ranks):
    if not pages or len(pages) <= 1:
        return pages
    else:
        pivot = ranks[pages[0]] #find pivot
        worse = []
        better = []
        for page in pages[1:]:
            if ranks[page] <= pivot:
                worse.append(page)
            else:
                better.append(page)
        return quicksort_pages(better, ranks) + [pages[0]] + quicksort_pages(worse, ranks)
```

Ok.  
주어진 값들을 받아서 정렬하는 문제였습니다 ㅎㅎ  
아니 근데 왜 새로운 함수를 만들지? 주어진거 안만들고;  