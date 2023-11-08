


## 의의
- R-CNN의 단점인
  1) RoI 마다 CNN연산을 함으로써 매우 느린 속도
  2) Multi-stage pipelines으로 모델을 한 번에 학습시키지 못함 을 개선함.

- 고정된 사이즈 문제를 해결하기 위해 **ROI Pooling**이라는 기법을 사용 함.
- RoI pooling, CNN 특징 추출, classification, bounding box regression까지 하나의 모델에서 학습함.


## Proecss 
1-1. R-CNN에서와 마찬가지로 Selective Search를 통해 RoI를 찾는다.
1-2. 전체 이미지를 CNN에 통과시켜 Feature Map을 추출한다.
3. Selective Search로 찾았던 RoI를 Feature Map 크기에 맞춰서 Projection 시킨다.
4. projection 시킨 RoI에 대해 RoI Pooling을 진행하여 고정된 크기의 feature vector를 얻는다.
5-1. 하나는 softmax를 통과하여 RoI에 대해 
5-2. Bounding box regression을 통해 Selective Search로 찾은 box의 위치를 조정한다.


- CNN을 통과한 feature map에서 2천 개의 

- 기존 R-CNN과 마찬가지로 Selective Search를 사용하여 영역을 제안(Region Proposal) 하였으나, 차이점은 간단하게 CNN을 병렬적으로 수행하느냐 라고 생각해볼 수 있음.
- 기존 R-CNN 같은 경우, Selective Search로부터 얻어진 2천 개의 영역을 각각 Crop & Resize하여 동일한 사이즈를 입력으로 사용
- 하지만 한 이미지 당 2천 번의 CNN을 수행함으로 매우 느릴 수 밖에 없었고, 이를 해결하기 위해 Fast R-CNN에서는 해당 영역(초록색 박스)의 Feature를 원본 이미지에서 추출하는 것이 아니라 **Feature Map 단에서 추출함.**
- 그렇기 때문에, 입력 이미지마다 단 한번의 CNN만을 수행하면 됨.
- 그리고 Feature Map에 해당 영역을 RoI Projection하면, 원본에서 Selective Search로 제안된 영역을 Feature Map Level에 투영시킬 수 있음. 

## RoI Pooling 
![image](https://github.com/sandartchip/TIL/assets/15938354/089fba79-2f55-4f41-9626-ba82a544418a)

- Fast R-CNN에서 먼저 입력 이미지를 CNN에 통과시켜 feature map을 추출한다.
- 그 후 이전에 미리 Selective Search로 만들어놨던 RoI(=region proposal)을 feature map에 projection 시킴. 
- 원래 ROI pooling을 이용함으로써 원래 이미지를 CNN에 통과시킨 후 나온 feature map에 이전에 
- Fast R-CNN은 1개의 피라미드를 적용시킨 SPP로 구성 됨.
- Fast R-CNN에서 적용된 1개의 피라미드 SPP로 고정된 크기의 feature vector를 만드는 과정을 "RoI Pooling"이라고 함.

- 

- 원래 이미지를 CNN에 통과시킨 후 



### 참고자료
https://ganghee-lee.tistory.com/36
