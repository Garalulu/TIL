# Python and Django

## 4-18. Forms

Type
- color : 색깔 지정
- text : 텍스트 입력

```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Forms</title>
  </head>
  <body>
    <form>
      <p>Enter Email:</p>
      <input type="email" name="useremail" value="">
      <input type="submit" name="" value="Submit">
    </form>

  </body>
</html>
```

입력 후 URL에 ?useremail=[something]%40[something]이 달린다.  

form action="url" method="get"  
-> 페이스북 홈피로 연결되며 뒤에 ?[name]="[something]" 붙는다.

label

텍스트와 여러 디자인 폼을 묶어서 쉽게 반복 생성하게 하는 도구

label for=""와 input id=""를 맞춰준다.  

input placeholder=""는 value와 달리 '미리보기' 개념
input required 할시 반드시 입력