## 개요
- SAM (Segment Anything Model)
- 어떤 이미지든 분할(segment)하는 것을 목표로 함. 
- 여기서의 이미지 분할이란, 이미지 내의 픽셀이 어떤 물체에 속하는지 식별하는 작업. 
- SAM은 '물체가 무엇인지'에 대한 일반적인 개념을 학습했으며, 트레이닝 중에 접해보지 못한 물체와 이미지 유형을 포함하여 모든 이미지 또는 비디오의 모든 물체에 대한 마스크를 생성할 수 있다.
- SAM은 객체가 무엇인지에 대한 일반적인 개념을 학습하고, 어떤 object에 관계없이 mask를 생성할 수 있음. 
- 수중 사진, 세포 현미경 등 새로운 이미지 도메인에 추가적인 트레이닝 없이 바로 사용 가능. (zero-shot transfer)

## SAM이 해결한 것
- 대화형 분할(Interactive Segmentation)
- 자동 분할(Automatic Segmentation)

## SAM의 기능
1) 어떤 사물이든 클릭 한 번으로 **이미지를 분할**
2) 분할 대상 사물이 모호한 경우에, 여러 개의 유효한 **마스크를 출력**
3) 이미지 내의 모든 사물을 자동으로 찾아서 마스킹
4) 실시간으로 입력된 정보를 바탕으로 이미지를 분할하기 때문에, 입력한 정보에 따라 이미지가 어떻게 분리되는지 빠르게 확인 가능

예시)
![image](https://user-images.githubusercontent.com/15938354/231387776-98ae72ff-e604-4d87-980d-bbd219aae0b3.png)


## Model 
![image](https://user-images.githubusercontent.com/15938354/230805910-d863352a-48b6-48e0-be59-67a79e4c001e.png)
- Segment Anything 모델은 두 개의 영역으로 나뉘어진다. 
- 이미지를 강력한 시맨틱 공간으로 featurize하여 downstream 작업에 사용함. 

## 인코더 종류
- SAM 모델은 3개의 다른 인코더에 로딩 된다 - ViT-B, ViT-L, ViT-H. 
- ViT-H는 Vit-B를 양적으로 향상시킨 것. 
- 이 인코더들은 다른 파라미터 갯수를 갖고 있다. 
- ViT-B having 91M, ViT-L having 308M, and ViT-H having 636M parameters.
- 
## Dataset 
- 광범위한 애플리케이션을 지원하고 컴퓨터 비전을 위한 기초 모델에 대한 추가 연구를 촉진하기 위한 일반 Segment Anything 모델(SAM)과 역대 최대 규모의 세분화 데이터세트인 Segment Anything 10억 Mask 데이터세트(SA-1B)을 공개하고 있음.
- The SA-1B Dataset 은 11 million licensed and privacy-preserving images들에서 1.1 billion segmentation mask를 포함함. 



https://discuss.pytorch.kr/t/sa-segment-anything/1362
https://blog.roboflow.com/segment-anything-breakdown/
https://brunch.co.kr/@f7413a9d5cff457/32
