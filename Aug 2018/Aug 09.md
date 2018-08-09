# Python and Django

## 5-23. CSS

CSS : Cascading Style Sheets  

HTML 구성요소를 디자인하는 방법

주로 html 파일과 별개로 .css 파일을 만들어 연결시킨다.

link : css와 html을 연결시켜주는 태그

```
<link rel="stylesheet" href="">
```

Ctrl+4+/ : 주석으로 변환

Basic Format
```
selected tag{
    property: value;  
}
```

color : 해당 태그의 색깔 변경. 색깔명, rgb, hex code, rgba로 변경 가능

```
h1{
    color: red;
}

li{
    color: rgb(8,84,1);
}

p{
    color: #0895a8;
}

h4{
    color: rgba(255, 97, 0.1) /* 0 : 투명, 1: 일반 rgb */
}
```

## 5-25. CSS lv2

background-color : 배경색. background로도 사용 가능. 이 때 url로 이미지를 배경으로 쓸 수 있다.  
background-repeat : 바둑판식 배열 등 배경 배치를 어떻게 할지 결정.  
border-color : 가장자리 색  
border-width : 가장자리 두께. medium ~ thick 또는 px로 표현   
border-style : 가장자리 스타일

div나 span으로 원하는 파트 스타일을 변경 가능하다.

```
body{
  background: url(http://static.asiawebdirect.com/m/phuket/portals/kosamui-com/homepage/beaches/pagePropertiesImage/samui-beaches.jpg.jpg);
  background-repeat: no-repeat;
}

div{
  background-color: blue;
  border-color: orange;
  border-width: 3px;
  border-style: double;
}

p{
  color: yellow;
}

span{
  background: red;
  color: black;
}
```
