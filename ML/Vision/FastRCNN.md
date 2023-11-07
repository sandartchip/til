

## 의의
- R-CNN의 단점인 매우 느린 속도를 개선한 논문.
- 고정된 사이즈 문제를 해결하기 위해 ROI Pooling이라는 기법을 사용 함. 
- 기존 R-CNN과 마찬가지로 Selective Search를 사용하여 영역을 제안(Region Proposal) 하였으나, 차이점은 간단하게 CNN을 병렬적으로 수행하느냐 라고 생각해볼 수 있음.
- 기존 R-CNN 같은 경우, Selective Search로부터 얻어진 2천 개의 영역을 각각 Crop & Resize하여 동일한 사이즈를 입력으로 사용
- 하지만 한 이미지 당 2천 번의 CNN을 수행함으로 매우 느릴 수 밖에 없었고, 이를 해결하기 위해 Fast R-CNN에서는 해당 영역(초록색 박스)의 Feature를 원본 이미지에서 추출하는 것이 아니라 **Feature Map 단에서 추출함.**
- 그렇기 때문에, 입력 이미지마다 단 한번의 CNN만을 수행하면 됨.
- 그리고 Feature Map에 해당 영역을 RoI Projection하면, 원본에서 Selective Search로 제안된 영역을 Feature Map Level에 투영시킬 수 있음. 

## RoI Pooling 

- Fast R-CNN은 1개의 피라미드를 적용시킨 SPP로 구성 됨.
- Fast R-CNN에서 적용된 1개의 피라미드 SPP로 고정된 크기의 feature vector를 만드는 과정을 "RoI Pooling"이라고 함.

- 

- 원래 이미지를 CNN에 통과시킨 후 
