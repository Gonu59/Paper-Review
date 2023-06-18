# Multi-Task Sparse Learning with Beta Process Prior for Action Recognition 리뷰
C Yuan 저술 · CVPR 2013 · 48회 인용
## Abstract   
human action recognition 분야에 **multi task sparse learning**을 제안하였다. 이는 최대한 적은 base로 다양한 특성을 갖는 테스트 샘플을 구성하게 한다.   
또한 모델 맨 앞단에 간결한 dictionary를 효율적으로 학습하고 모든 task에서 공유되는 sparse 구조를 추론하기 위해 **Beta Process prior**이라는 parameter를 제시한 논문이다.      
KTH 및 UCF sports dataset 으로 실험을 하였다.

## Introduction
### The Fusion of Multiple Features
single feature based representation만으로는 시각적변화(시점, 조명 등)을 파악하기가 쉽지 않기에 multiple feature들의 결합이 액션 인식에 효과적이다.    
기존 연구들은 색, 질감, 모양 특징들을 이용하거나[Yuan et al], 비디오 시퀀스를 여러 부분 motion descriptor로 표현 하고 이런 descriptor를 sparse representation으로 인코딩해 분류했다[Tran et al].
이런 모델들은 각 part motion descriptor에 독립적으로 sparse representation을 적용하지만, 실제로는 각 부분들끼리 서로 연관되어 있다.

### Multi-Task Sparse Learning with Beta Process Prior


