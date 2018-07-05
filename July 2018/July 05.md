# Machine Learning

## 텐서플로우 첫걸음

텐서플로우 : 머신러닝 개발 플랫폼

estimator API

## 도구

텐서플로우 도구함 계층구조

에스티메이터(tf.estimator): 높은 수준의 OOP API  
tf.layer/tf.losses/tf.metrics: 일반 모델 구성요소용 라이브러리  
텐서플로우: 낮은 수준의 API

텐서플로우
- 그래프 프로토콜 버퍼
- 분산된 그래프를 실행하는 런타임

추상화 수준이 높을수록 더 사용하기 쉽지만 설계상 유연성이 떨어진다. 특별한 모델링 무제를 해결하기 위해 더 유연한 추상화가 필요하면 한 수준 아래로 이동해가며 제작하는게 합리적이다.

tf.estimator API  
구현된 선형 회귀 프로그램의 형식
```
import tensorflow as tf

# Set up a linear classifier.
classifier = tf.estimator.LinearClassifier()

# Train the model on some example data.
classifier.train(input_fn=train_input_fn, steps=2000)

# Use it to predict.
predictions = classifier.predict(input_fn=predict_input_fn)
```

Pandas 간단 소개

열 중심 데이터 분석 API. 입력 데이터를 처리하고 분석하는 데 효과적이다.

API 버전 출력 코드
```
import pandas as pd
pd.__version__
```

Pandas의 기본 데이터 구조는 두 가지 클래스로 구현된다.
DataFrame은 행 및 이름이 지정된 열이 포함된 관계형 데이터 테이블이다.
Series는 하나의 열이다. DataFrame에는 하나 이상의 Series와 각 Series의 이름이 포함된다.

Series 생성 예
```
pd.Series(['San Francisco', 'San Jose', 'Sacramento'])
```

string 열 이름과 매핑되는 'dict'를 각각의 Series에 전달하여 만들 수 있다. 길이가 일치하지 않는 경우, 누락된 값은 특수 NA/NaN값으로 채워진다.

dict 생성 후 출력 예제
```
city_names = pd.Series(['San Francisco', 'San Jose', 'Sacramento'])
population = pd.Series([852469, 1015785, 485199])

pd.DataFrame({ 'City name': city_names, 'Population': population })
```

대부분의 경우 파일을 DataFrame으로 로드해 처리한다.

DataFrame.describe는 그에 관한 통계를 보여준다.
```
california_housing_dataframe = pd.read_csv("https://storage.googleapis.com/mledu-datasets/california_housing_train.csv", sep=",")
california_housing_dataframe.describe()
```

DataFrame.head는 DataFrame 레코드 중 처음 몇 개만 표시한다.
```
california_housing_dataframe.head()
```

DataFrame.hist는 한 열에서 값의 분포를 빠르게 검토할 수 있다.
```
california_housing_dataframe.hist('housing_median_age')
```

Python dict/list 작업으로 DataFrame 데이터에 엑세스할 수 있다.
```
cities = pd.DataFrame({ 'City name': city_names, 'Population': population })
print type(cities['City name'])
cities['City name']
```
```
print type(cities['City name'][1])
cities['City name'][1]
```
```
print type(cities[0:2])
cities[0:2]
```

Python의 기본 산술 연산이나 Numpy도 Series에 적용할 수 있다.
```
import numpy as np

np.log(population)
```

lambda 함수도 가능하다.
인구가 백만명을 초과하는지 나타내는 새 Series 만들기
```
population.apply(lambda val: val > 1000000)
```

기존 DataFrame에 새 Series 추가하기
```
cities['Area square miles'] = pd.Series([46.87, 176.53, 97.92])
cities['Population density'] = cities['Population'] / cities['Area square miles']
cities
```

다음 두 명제 모두 True인 경우에만 True인 새 부울 열을 추가하여 도시 테이블을 수정합니다.
- 도시 이름은 성인의 이름을 본따서 지었다.
- 도시 면적이 130제곱킬로미터보다 넓다.

```
cities['Is wide and has saint name'] = (cities['Area square miles'] > 50) & cities['City name'].apply(lambda name: name.startswith('San'))
cities
```

index 속성을 정의해 데이터의 순서를 재정렬할 수 있다. 기본적으로 생성 시 Pandas는 소스 데이터의 순서를 나타내는 색인 값을 할당하기 때문에 색인값은 고정된다.

```
city_names.index
cities.index
```

수동으로 행 순서 재정렬
```
cities.reindex([2, 0, 1])
```

색인 값에 없는 값 포함 시 누락된 색인에 새 행을 추가하고 모든 해당 열을 NaN값으로 채운다.