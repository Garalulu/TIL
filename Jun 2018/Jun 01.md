# Python

## 22 - 21. Page Rank

Ranking web pages  
앞에서 보았듯이 popular 지수를 이제 page에 직접 적용한다.  
모든 웹 페이지가 동일한 비중의 영향력을 가지고 있지 않으니 이용  
outlink가 없는 페이지가 있는 경우는 다음에 생각해보도록 하자  
```
rank(0,url) -> 1
rank(t,url) -> 모든 inlinks[url] in p를 rank(t-1,p) / outlinks[p]
```

## 22 - 22. Altavista

```
What is AltaVista?
```
https://en.wikipedia.org/wiki/AltaVista
검색 엔진 회사로 2013년에 마지막으로 서비스를 중단함.  
1998년에 가장 인기있는 검색 엔진  
page에 같은 단어를 여러 번 작성하면 적게 작성한 거보다 중요도가 커지는 문제 = measure of popularity or traffic

## 22 - 23. Urank

Implementing URank  
페이지 간 연결고리를 Graph로 표현  
Graph : Edge들로 연결된 Nodes  

Nodes
```
{url:[pages it links to], ...}
```

Building the Link Graph
```
crawl_web(seed) -> index, graph
```

기존에 있는 crawl_web을 변형시켜 새로운 Dictionary를 만들고 리턴하게 한다.

## 22 - 24. Implementing Urank

```
# Modify the crawl_web procedure so that instead of just returning the 
# index, it returns an index and a graph. The graph should be a 
# Dictionary where the key:value entries are:

#  url: [list of pages url links to] 


def crawl_web(seed): # returns index, graph of outlinks
    tocrawl = [seed]
    crawled = []
    graph = {}  # <url>:[list of pages it links to]
    index = {} 
    while tocrawl: 
        page = tocrawl.pop()
        if page not in crawled:
            content = get_page(page)
            add_page_to_index(index, page, content)
            outlinks = get_all_links(content)
            
            #Insert Code Here
            
            union(tocrawl, outlinks)
            crawled.append(page)
    return index, graph


cache = {
   'http://udacity.com/cs101x/urank/index.html': """<html>
<body>
<h1>Dave's Cooking Algorithms</h1>
<p>
Here are my favorite recipes:
<ul>
<li> <a href="http://udacity.com/cs101x/urank/hummus.html">Hummus Recipe</a>
<li> <a href="http://udacity.com/cs101x/urank/arsenic.html">World's Best Hummus</a>
<li> <a href="http://udacity.com/cs101x/urank/kathleen.html">Kathleen's Hummus Recipe</a>
</ul>

For more expert opinions, check out the 
<a href="http://udacity.com/cs101x/urank/nickel.html">Nickel Chef</a> 
and <a href="http://udacity.com/cs101x/urank/zinc.html">Zinc Chef</a>.
</body>
</html>






""", 
   'http://udacity.com/cs101x/urank/zinc.html': """<html>
<body>
<h1>The Zinc Chef</h1>
<p>
I learned everything I know from 
<a href="http://udacity.com/cs101x/urank/nickel.html">the Nickel Chef</a>.
</p>
<p>
For great hummus, try 
<a href="http://udacity.com/cs101x/urank/arsenic.html">this recipe</a>.

</body>
</html>






""", 
   'http://udacity.com/cs101x/urank/nickel.html': """<html>
<body>
<h1>The Nickel Chef</h1>
<p>
This is the
<a href="http://udacity.com/cs101x/urank/kathleen.html">
best Hummus recipe!
</a>

</body>
</html>






""", 
   'http://udacity.com/cs101x/urank/kathleen.html': """<html>
<body>
<h1>
Kathleen's Hummus Recipe
</h1>
<p>

<ol>
<li> Open a can of garbanzo beans.
<li> Crush them in a blender.
<li> Add 3 tablespoons of tahini sauce.
<li> Squeeze in one lemon.
<li> Add salt, pepper, and buttercream frosting to taste.
</ol>

</body>
</html>

""", 
   'http://udacity.com/cs101x/urank/arsenic.html': """<html>
<body>
<h1>
The Arsenic Chef's World Famous Hummus Recipe
</h1>
<p>

<ol>
<li> Kidnap the <a href="http://udacity.com/cs101x/urank/nickel.html">Nickel Chef</a>.
<li> Force her to make hummus for you.
</ol>

</body>
</html>

""", 
   'http://udacity.com/cs101x/urank/hummus.html': """<html>
<body>
<h1>
Hummus Recipe
</h1>
<p>

<ol>
<li> Go to the store and buy a container of hummus.
<li> Open it.
</ol>

</body>
</html>




""", 
}

def get_page(url):
    if url in cache:
        return cache[url]
    else:
        return None
    
def get_next_target(page):
    start_link = page.find('<a href=')
    if start_link == -1: 
        return None, 0
    start_quote = page.find('"', start_link)
    end_quote = page.find('"', start_quote + 1)
    url = page[start_quote + 1:end_quote]
    return url, end_quote

def get_all_links(page):
    links = []
    while True:
        url, endpos = get_next_target(page)
        if url:
            links.append(url)
            page = page[endpos:]
        else:
            break
    return links


def union(a, b):
    for e in b:
        if e not in a:
            a.append(e)

def add_page_to_index(index, url, content):
    words = content.split()
    for word in words:
        add_to_index(index, word, url)
        
def add_to_index(index, keyword, url):
    if keyword in index:
        index[keyword].append(url)
    else:
        index[keyword] = [url]

def lookup(index, keyword):
    if keyword in index:
        return index[keyword]
    else:
        return None



index , graph = crawl_web('http://udacity.com/cs101x/urank/index.html') 

if 'http://udacity.com/cs101x/urank/index.html' in graph:
    print graph['http://udacity.com/cs101x/urank/index.html']
#>>> ['http://udacity.com/cs101x/urank/hummus.html',
#'http://udacity.com/cs101x/urank/arsenic.html',
#'http://udacity.com/cs101x/urank/kathleen.html',
#'http://udacity.com/cs101x/urank/nickel.html',
#'http://udacity.com/cs101x/urank/zinc.html']
```
graph[page]=outlinks
key 'page'마다 그 page에서 나온 링크들을 저장

# Summary
검색 엔진에서 상위노출되는 기준을 설정하고자 함. Altavista는 단순 키워드 누적이 높을수록 상위로 올려서 그 검색어를 도배만 하면 위로 올라가는 단점이 있었다. 옛날에 블로그들을 볼 때 검색 상위 노출을 위해 키워드들을 스팸하는 글들을 여럿 본 적이 있는데, 이 시스템을 악용한 것이였다고 깨달았다.