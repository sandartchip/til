### 전이학습(Transfer Learning)의 활용
전이학습을 활용한다면 아래와 같이 활용해볼 수 있겠다.

1. 모델(ResNet 등)을 불러 와 그대로 분류할 데이터 입력 후 분류 진행(학습 X)
2. 모델을 불러온 후, 최상위 층(분류기)만 용도대로 재설정하여 학습.  
이 때 불러온 전이학습 모델은 가중치를 동결(freeze)해 학습시키지 않고, Classifier 혹은 이후 추가한 fully connected layer의 weight만 학습하여 사용
3. 2번과 동일하게 진행한 후, 동결해 두었던 전이학습 모델의 가중치를 (일부 또는 전부) Training 가능한 상태로 만들고, 학습하도록 한다.
 (일부 또는 전체) 부분은 정해진 답이 없어 딱 잘라 말할 수 없다. 
 

#### Pytorch의 pretrained=True 옵션
- 모델을 초기화시킬  weight를 기존의 데이터로 트레이닝된 parameter value로 initialize하는 것.
- 이후에 모델 구조에 따라 weight가 바뀔 지 안 바뀔지가 결정됨.
- 만약 모든 layer를 전부 freeze시키면 weight는 ImageNet을 트레이닝 시킨 값 그대로임.

참고: https://velog.io/@dlskawns/Deep-Learning-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%B2%98%EB%A6%AC-%EC%A0%84%EC%9D%B4%ED%95%99%EC%8A%B5Transfer-Learning-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EB%B6%84%EB%A5%98-%EB%AA%A8%EB%8D%B8-%EA%B5%AC%ED%98%84-%EC%8B%A4%EC%8A%B5
