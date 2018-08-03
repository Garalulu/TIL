# Python and Django

## 4-15. Tables

```
<table> '# border=""'로 경계선 생성. 숫자 커질수록 경계선 두께 증가
    <thead> # 테이블 머리. 구성원 글씨보다 두꺼움 (없이도 만들기 가능)
        <th></th>
    </thead>
    <tr>
        <td></td>
    </tr>
</table>
```
표 구성표

QUIZ
```
Pop Quiz!


Use the following information to make a
table about Country GDP.

Source for data below:
https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(nominal)

Make a table with HTML consisting of 3 columns:
Country Name
Country Flag
GDP (millions of USD)

Your table will have 3 rows.
Use the information below to attribute the cells correctly:

United States
US Flag: "https://upload.wikimedia.org/wikipedia/en/thumb/a/a4/Flag_of_the_United_States.svg/190px-Flag_of_the_United_States.svg.png"
GDP: 18,561,930

India
Indian Flag: "https://upload.wikimedia.org/wikipedia/en/thumb/4/41/Flag_of_India.svg/150px-Flag_of_India.svg.png"
GDP: 2,250,990

United Kingdom
UK Flag: "https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/200px-Flag_of_the_United_Kingdom.svg.png"
GDP: 2,649,890
```

Answer
```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Tables Test</title>
  </head>
  <body>
    <table border="1">
      <thead>
        <th>Name</th>
        <th>Flag</th>
        <th>GDP</th>
      </thead>
      <tr>
        <td>United States</td>
        <td><img src="https://upload.wikimedia.org/wikipedia/en/thumb/a/a4/Flag_of_the_United_States.svg/190px-Flag_of_the_United_States.svg.png" alt=""></td>
        <td>18,561,930</td>
      </tr>
      <tr>
        <td>India</td>
        <td><img src="https://upload.wikimedia.org/wikipedia/en/thumb/4/41/Flag_of_India.svg/150px-Flag_of_India.svg.png" alt=""></td>
        <td>2,250,990</td>
      </tr>
      <tr>
        <td>United Kingdom</td>
        <td><img src="https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/200px-Flag_of_the_United_Kingdom.svg.png" alt=""></td>
        <td>2,649,890</td>
      </tr>
    </table>

  </body>
</html>
```

## 4-18. Forms

```
<form>
    <input type="" name="" value="">
</form>
```

Type
- email : @가 있어야 제출 가능
- password : 모든 글자가 보이지 않음
- submit : 제출용도

value로 미리 입력될 글자나 submit 버튼에 새겨질 글자 정함.