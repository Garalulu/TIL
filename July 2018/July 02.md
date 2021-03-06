# Machine Learning

## ML 소개
Peter Norvig: Google 머신 러닝 책임자

머신러닝을 배워서 좋은 점 3가지
1. 프로그래밍 시간을 줄일 수 있는 도구 획득
2. 제품을 맞춤 설정하여 특정 집단의 사용자에게 잘 맞는 제품을 제공할 수 있음
3. 프로그래머로서 수동으로 할 방법이 없어 보이는 문제 해결 가능

## ML 문제로 표현하기

기본 프레임워크: 지도 머신러닝  
입력을 결합하여 모델을 만들고 이전에 보지 못한 데이터도 적절히 예측하는 방법

라벨: 예측하는 실제 항목(y)
- 기본 선형 회귀의 y 변수  
e.g) 스팸 or 스팸 아님 case: email spam filtering, 밀의 향후 가격, 사진에 표시되는 동물의 종류, 오디오 클립의 의미 등등 무엇이든지 가능  

특성: 데이터를 설명하는 입력 변수(xi)
- 기본 선형 회귀의 {x1, x2, ... xn} 변수
e.g) 이메일에 포함된 단어, 발신 및 수신 주소, 이메일이 전송된 시간, '이상한 속임수 하나'라는 구문이 포함된 이메일

예: 데이터(x)의 특정 인스턴스  

라벨 있는 예: {특성, 라벨}(x, y)
- 모델 학습용  
e.g) 사용자가 명시적으로 '스팸' or '스팸 아님'으로 표시한 개별 이메일

라벨 없는 예: {특성, ?}(x, ?)
- 새 데이터 예측용. 라벨이 있는 예로 모델을 학습시킨 다음 해당 모델을 사용하여 라벨이 없는 예의 라벨을 예측한ㄷ나.

모델: 예를 예측된 라벨(y')에 매핑
- 학습되는 내부 매개변수에 의해 정의
- 학습: 모델을 만들거나 배우는 것. 라벨이 있는 예를 모델에 보여 주고 모델이 특성과 라벨의 관계를 점차적으로 학습하도록 한다.
- 추론: 학습된 모델을 라벨이 없는 예에 적용하는 것. 학습된 모델을 사용하여 유용한 예측(y')을 해낸다.

회귀 모델: 연속적인 값 예측  
- e.g) 캘리포니아의 주택 가격이 얼마인가요?  
사용자가 이 광고를 클릭할 확률이 얼마인가요?

분류 모델: 불연속적인 값 예측
- 주어진 이메일 메시지가 스팸인가요, 스팸이 아닌가요?
- 이 이미지가 강아지, 고양이 또는 햄스터의 이미지인가요?

## 이해도 확인

1. 주어진 이메일이 '스팸' 인지 '스팸이 아닌지' 예측하기 위해 지도 머신러닝 모델을 개발한다고 합시다. 다음 중 참인 내용은 무엇일까요?

- 모델을 학습시키는 데는 라벨이 없는 예를 사용합니다. (X)  
학습시키는 데는 라벨이 있는 예를 사용
- 제목 헤더의 단어는 라벨로 사용하기에 적절합니다. (X)  
특성으로 사용하기엔 적절함
- 일부 라벨은 신뢰할 수 없을 수도 있습니다. (O)  
확실히 이 데이터 세트의 라벨은 특정 이메일 메시지를 스팸으로 표시하는 이메일 사용자로부터 가져온 것일 수도 있습니다. 의심스러운 모든 이메일 메시지를 스팸으로 표시하는 사용자는 아주 적기 때문에 특정 이메일이 스팸인지 확인하기 어려울 수도 있습니다. 또한 일부 스팸 발송자나 봇넷은 결함이 있는 라벨을 제공하여 모델을 고의적으로 손상시킬 수 있습니다.
- 스팸' 또는 '스팸 아님'으로 표시되지 않은 이메일은 라벨이 없는 예입니다. (O)  
라벨 값이 표시되지 않았으므로 없는 예다.

2. 한 온라인 신발가게에서 사용자에게 맞춤형 신발을 추천하는 지도 ML 모델을 만들려고 합니다. 즉 이 모델에서는 철수에게 특정 신발을 추천하고 영희에게는 다른 신발을 추천합니다. 다음 중 참인 내용은 무엇일까요?
- 신발 크기는 유용한 특성입니다. (O)  
신발 크기는 추천된 신발이 사용자의 마음에 들 것인지 쉽게 확인할 수 있는 수량화 가능한 신호입니다. 
- 사용자가 아주 좋아하는 신발은 유용한 라벨입니다. (X)  
좋아함은 관찰 가능하고 수량화 가능한 측정항목이 아닙니다.
- 신발의 아름다움은 유용한 특성입니다. (X)  
구체적이고 수량화 가능한 특성이 좋은 특성입니다. 아름다움은 너무 모호한 개념이어서 특성으로 사용하기에 적절하지 않습니다. 
- 사용자의 신발 설명 클릭수는 유용한 라벨입니다. (O)  
사용자는 마음에 드는 신발의 설명만 읽으려 할 것입니다. 따라서 사용자 클릭수는 좋은 학습 라벨로 사용할 수 있는 관찰 가능하고 수량화 가능한 측정항목입니다.

## ML로 전환하기

주택 면적값을 입력하면 주택 가격을 예상하는 모델을 만들어 보자.

x = House Square Footage  
y = House Price  

이 표에 해당하는 그래프를 그려보자.  
y = wx + b  
그 중 실제 y값과 그 위치에서의 그래프값의 차를 '손실'이라고 한다.  
주어진 예의 L2 손실은 제곱 오차라고도 한다.  
= 예측과 라벨 간의 차이 제곱  
= (관찰 - 예측)^2  
= (y = y')^2

## 선형 회귀

y' = b + w1x1

y' = 예측된 라벨(얻고자 하는 출력)  
b = 편향(y절편), (w_0\)로도 표현  
w1 = 특성 1의 가중치  
x1 = 특성(알려진 입력)  

세 가지 특성에 의존하는 모델은 다음과 같은 방정식을 사용한다.

y' = b + w1x1 + w2x2 + w3x3

## 학습 및 손실

모델을 학습시킨다: 라벨이 있는 데이터로부터 올바른 가중치와 편향값을 학습(결정)한다  

지도 학습에서 머신러닝 알고리즘은 다양한 예를 검토하고 손실을 최소화하는 모델을 찾아봄으로써 모델을 만들어낸다. a.k.a 경험적 위험 최소화  

손실: 잘못된 예측에 대한 `벌점`  
모델 학습의 목표느 모든 예에서 평균적으로 작은 손실을 갖는 가중치와 편향의 집합을 찾는 것이다.

제곱 손실(L2 손실)
```
= the square of the difference between the label and the prediction
= (observation - prediction(x))^2
= (y - y')^2
```

평균 제곱 오차(MSE): 예시당 평균 제곱 손실. 개별 예의 모드 제곱 손실을 합한 뒤 예의 수로 나누어 구한다.

MSE = 1/N * sigma {(x, y)는 D에 포함} (y - prediction(x))^2

(x, y) = 예(x: 특성 집합, y: 예의 라벨)  
prediction(x) = 특성 집합 x와 결합된 가중치 및 편향의 함수  
D = (x, y) 쌍과 같이 여러 라벨이 있는 예가 포함되 데이터 세트  
N = D에 포함된 예의 수

MSE는 머신 러닝에서 흔히 사용되지만, 모든 상황에서 최선인 유일한 손실 함수는 아니다.