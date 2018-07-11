# Python

## 27 - 4. Remove Tags

```
When we add our words to the index, we don't really want to include html tags such as <body>, <head>, <table>, <a href="..."> and so on.

Write a procedure, remove_tags, that takes as input a string and returns a list of words, in order, with the tags removed. Tags are defined to be strings surrounded by < >. Words are separated by whitespace or tags. 
You may assume the input does not include any unclosed tags, that is, there will be no '<' without a following '>'.
```

```
def remove_tag(string):
    start = string.find('<')
    while start != -1:
        end = string.find('>', start)
        string = string[:start] + " " + string[end + 1:]
        start = string.find('<')
    return string.split()
```
<와 >의 위치를 찾고 그 부분을 제외한 나머지 문장으로 구성한 뒤 띄어쓰기를 넣는다. split()은 특정 기호(띄어쓰기)로 구분되는 문자열을 전부 분리하는 함수니 딱이다


## 27 - 5. Date Converter

```
# Write a procedure date_converter which takes two inputs. The first is 
# a dictionary and the second a string. The string is a valid date in 
# the format month/day/year. The procedure should return
# the date written in the form <day> <name of month> <year>.
# For example , if the
# dictionary is in English,

english = {1:"January", 2:"February", 3:"March", 4:"April", 5:"May", 
6:"June", 7:"July", 8:"August", 9:"September",10:"October", 
11:"November", 12:"December"}

# then  "5/11/2012" should be converted to "11 May 2012". 
# If the dictionary is in Swedish

swedish = {1:"januari", 2:"februari", 3:"mars", 4:"april", 5:"maj", 
6:"juni", 7:"juli", 8:"augusti", 9:"september",10:"oktober", 
11:"november", 12:"december"}

# then "5/11/2012" should be converted to "11 maj 2012".

# Hint: int('12') converts the string '12' to the integer 12.
```

```
def date_converter(lang, data):
    first = data.find('/')
    month = data[:first]
    second = data.find('/', first+1)
    day = data[first+1:second]
    year = data[second+1:]
    
    return day + " " + lang[int(month)] + " " + year
```

dictionary 기능 활용해서 언어에 맞는 월 단어 출력

## 27 - 6. Termination

```
For each of the procedures defined below, check the box if the procedure always terminates for all inputs that are natural numbers (1,2,3...).

def proc1(n):
   while True:
      n = n - 1
      if n == 0:
         break
   return 3

def proc2(n):
   if n == 0:
      return n
   return 1 + proc2(n - 2)

def proc3(n):
   if n <= 3:
      return 1
   return proc3(n - 1) + proc3(n - 2) + proc3(n - 3)
```

proc1은 모든 수를 terminate
proc2는 n-2므로 1을 terminate 못함
proc3은 n-1, n-2, n-3을 모두 갖추어 모든 수 terminate