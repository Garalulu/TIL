# Python

## 22 - 25. Computing Page Rank

compute_ranks를 생성해 Page Rank를 매긴다.  
lookup_best를 생성해 best page를 추출한다.  
page rank 식은 `jun 01.md` 참조

## 22 - 26. Formal Calculations

```
#d = 0.8

rank(0,url) = 1/npages
newranks[url] = (1-d)/npages + inlinks to url p (d*rank[p]/# of outlinks from p)

#ranks : ranks at time t-1
#newranks : ranks at time t
```

## 22 - 27, 28. Computer Ranks (Urank)

```
def compute_ranks(graph):
    d = 0.8 # damping factor
    numloops = 10
    
    ranks = {}
    npages = len(graph)
    for page in graph:
        ranks[page] = 1.0 / npages
    
    for i in range(0, numloops):
        newranks = {}
        for page in graph:
            newrank = (1 - d) / npages
            
            #Insert Code Here
            for node in graph:
                if page in graph[node]:
                    newrank = newrank + d * (ranks[node] / len(graph[node]))
            newranks[page] = newrank
        ranks = newranks
    return ranks
```

## 22 - 29. Search Engine

Page Rank를 만들었지만 실제 value를 어떻게 하면 프로그램에 추가할 수 있을까?  
숙제 : 나만의 검색엔진 이름 짓기

# Summary

아직 Urank에 대한 계산식 자체를 이해하진 못했지만 어떻게 프로그래밍하는지는 알게 되었다. 검색 엔진이라는 개념은 내가 프로그래밍하고자 하는 것과는 다소 거리가 있는 내용이라 집중도가 떨어져서 그럴 수도 있다.  
다양한 알고리즘에 대해 공부할 필요성을 느꼈다. 마지막 단원 들어가기 전에 코딩에 집중해야겠다