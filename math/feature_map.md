
## Pooling Layers
![image](https://user-images.githubusercontent.com/15938354/217681427-bc87c67b-9b19-40e9-bed0-922a0f43e0ca.png)

- Pooling layer라 부르는 이 레이어는 주로 convolution layer를 input으로 받아들인다.
- 콘볼루션 레이어는 각 필터 당 하나의 feature map이 형성되고, 그 feature map을 스택처럼 쌓아둔 것이다.
- 많은 object 카테고리가 존재하는 복잡한 데이터셋을 가지고 CNN을 구현하는 경우 매우 많은 수의 필터를 필요로 하는데, 각각은 이미지의 패턴을 찾는데 유용하다. 

![image](https://user-images.githubusercontent.com/15938354/217681679-686ea480-823a-4b2b-9664-f92d299be202.png)

- 필터가 많다는 얘기는 그만큼 feature map이 쌓인다는 것이고, 이것은 우리가 구현할 CNN의 차원이 매우 크다는 얘기이다.
- 고차원(Higher dimensionality)를 구현하려면 그에 상응하는 더 많은 수의 파라미터를 필요로 함
- 많은 파라미터는 over-fitting초래
- 따라서 차원을 감소시킬 방법을 필요로 함
- 이 역할을 CNN에서 해주는 레이어가 pooling layer이다.


![image](https://user-images.githubusercontent.com/15938354/217681377-7fd75610-1efd-4f2b-a984-9ff7b0a00d47.png)




### Max Pooling lyaer
![image](https://user-images.githubusercontent.com/15938354/217681809-9fef184d-2a8b-4945-a51a-cfee8a578a62.png)
- feature map들이 쌓여 있는 스택을 input으로 받는다.
- window size와 stride를 필요로 함
- window 상에서 포함하고 있는 픽셀들 중 최대의 값을 뽑아낸다. 

### Global Average Pooling layer
![image](https://user-images.githubusercontent.com/15938354/217681825-3b8702f8-b9c8-4109-978f-05619161c425.png)
- window size나 stride 지정X
- global avergage pooling layer는 **각 feature map 상의 노드들의 평균을 뽑아낸다."
- 급격하게 CNN의 차원을 줄인다.
![image](https://user-images.githubusercontent.com/15938354/217681853-a65fb2ed-3926-49f1-b04d-e3612b1090e4.png)

- 두 Pooling layer은 모두 input의 차원을 줄여준다.

https://kevinthegrey.tistory.com/142
