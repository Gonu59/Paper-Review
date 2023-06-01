# A survey on Multi-Task Learning Review
Yu Zhang and Qiang Yang  1656회 인용 [31-05-23 기준]

## 1. Introduction
사람은 동시에 여러 task의 학습이 가능. 머신러닝에서도 인간과 같이 하나의 task의 학습에서의 지식이 다른 task에 영향이 있을 것이라 생각.

mtl의 동기는 데이터 희소의 문제를 완화하고자임. mtl은 모든 task에서 데이터를 종합해서 사용하기에 각 task에서 더 정확한 결과를 낼 수있다. 이 관점에서 mtl은 data cost를 줄일 수 있음. 데이터가 많다면 더 robust하게 학습하고 강력한 모델학습이 가능하다. knowledge sharing을 통해 더 높은 퍼포먼스와 오버피팅을 방지할 수 있다.

### 유사한 학습 방식과의 차이점

#### transfer learning

- MTL: task 간의 구분이 없고 전체 tasks의 성능을 올리는 게 목적   
- TF: source task의 도움을 받아 target task의 성능을 올림. 즉, source task의 성능 향상은 뒷전   

#### continual learning

- 각각의 task에 대한 학습이 순차적으로 이뤄지는 반면 mtl은 한번에 학습이 이루어짐
#### Multi label learning/ Multi-output regression

- 각각의 label을 하나의 task로 취급하면 MTL의 특수한 경우로 생각할 수 있음
#### Multi view learning

- 각각의 data point는 여러 view 이며 각 view는 feature set임. view마다 feature set이 다르지만 하나의 task에 대한 학습임. 즉 여러 data가 여러 task에 영향을 끼치는 mtl과 다름.

본문에서는 MTL에 대해 알고리즘 모델링과 응용, 이론적 분석으로 조사를 한다.   

**알고리즘 모델링**에는 다음과 같은 방법들이 쓰인다.   
- feature learning approach, feature tranformation, feature selection approach
- low-rank approach
- task clustering
- task relation
- decomposition

## 2. MTL Models
### MTL의 정의
"모든 task 또는 그들의 subset이 연관되어 있는 m개의 learning tasks $\\{T_i\\}^m_i=1$이 주어졌을 때, MTL은 모든 task 또는 다른 task들과 서로 포함되는 knowledge를 이용하여 모든 각각의 task $T_i$에 대한 성능이 높아지는 것에 목적을 둔다."   
대부분의 mtl 연구가 supervised learning으로 setting되어 있기 때문에 이 섹션에선 supervised learning으로 초점을 맞춤.   

각각의 task $T_i$는 training dataset $D_i$ 를 수반한다.   
- homogeneous-feature MTL: 서로 다른 task가 동일한 feature space에 있는 경우   
- heterogeneous-feature MTL: 서로 다른 task가 다른 feature space에 있는 경우   
일반적인 경우 homogeneous-feature MTL이다. 








