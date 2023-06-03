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

MTL의  정의를 이해하기 위해서는 세 가지 문제에 대해 이해해야 한다. 세가지 문제는 **'When to Share' 'What to Share' 'How to Share'** 이다.
#### When to Share
언제 공유하나라는 문제는 multi task problem에서 single task와 multi task 모델 중 어느 걸 선택하냐는 문제다.    
현재 이런 결정은 전문가가 결정하고 관련 연구가 적다. 간단한 해결책은 model selection problem으로 생각하는 것이지만 계산량이 많고 더 많은 데이터를 요구할 수 있다.
    
#### What to Share
무엇을 공유하냐는 문제는 모든 task에서 일어나는 지식을 어떤 형태로 공유하냐는 문제이다. 형태에는 'feature', 'instance', 'parameter'가 있다.
- feature based MTL: 다른 task들이 공통된 feature를 학습하는데 목표
- instance based MTL: 한 작업에서 다른 작업에 유용한 data instance를 식별하여 그를 공유함.
- parameter based MTL: 모델 매개변수를 사용하여(ex: weights) 정규화 같은 방식으로 다른 task의 parameter를 학습하는데 도움.
기존 MTL 연구는 feature 또는 parameter 기반 연구임.

#### How to Share
어떻게 공유하는 지에 대한 문제는 knowledge share에 대한 구체적 방안 제시이다. 
feature-based MTL에는 중요한 접근법으로 feature learning approach가 있다. 
feature learning approach는 shallow 또는 deep model에서 여러 작업에 대한 common feature representation을 학습하는데 중점을 맞춘다.

parameter-based MTL에는 주요 접근법으로 다음 4가지가 있다.
- low-rank approach: 여러 task의 관련도를 parameter matrix의 low rankness로 해석한다.
- task clustering approach: 비슷한 task 끼리 task cluster로 만든다
- task relation learning approach: 데이터에서 task들 사이의 정량적 관계에 대해 학습하는걸 목표로 한다.
- decomposition approach: 모든 작업의 모델 파라미터를 두 개 이상의 구성 요소로 분해하며, 이 구성 요소는 서로 다른 정규화에 의해 페널티를 받는다.

### 2.1 Feature Learning Approach



