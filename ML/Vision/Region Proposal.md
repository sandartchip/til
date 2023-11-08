


# Region Proposal 

- 기존에는 이미지에서 object detection을 위해 sliding window 방식을 이용했었는데, Sliding Window 방식의 비효율성을 개선하기 위해 
'물체가 있을 만한' 영역을 빠르게 찾아내는 알고리즘이 region proposal이다.

- Image Crop과 Warp을 적용하여 2000개의 Region 영역을 Proposal한다.
- 즉, regional proposal은 object의 위치를 찾는 localization 문제이다.

# 예시
- Selective search, Edge boxes가 있다.

## 방법 1) Selective Search
- 원본 이미지로부터 최초 Segmentation을 수행하고, 이를 통해 후보 Object를 추출하는 기법.
- Color, 무늬(Texture), 크기(Size), 형태(Shape)에 따라 유사한 Region을 계층적 그룹핑으로 계산함. 



## 참고자료
https://rubber-tree.tistory.com/133#:~:text=Selective%20Search%EA%B8%B0%EB%B2%95%EC%9D%B4%EB%9E%80%20Region,%EB%A5%BC%20%EC%B6%94%EC%B6%9C%ED%95%98%EB%8A%94%20%EA%B8%B0%EB%B2%95%EC%9D%B4%EB%8B%A4.
