![image](https://user-images.githubusercontent.com/15938354/175475132-66f3ee6d-c341-47ea-95c7-e54ae5debe2e.png)


이미지를 입력으로 받고, convolution을 해서 feature map들을 얻는다.

### Stride 
- 스트라이드 : 보폭
- 필터를 적용하는 간격.
- 스트라이드를 크게 하면 출력 데이터의 크기는 작아진다. 

subsampling을 한 뒤 linear layer로 이어져서, classification을 수행한다.


![image](https://user-images.githubusercontent.com/15938354/175477871-81f8bde5-2cb3-4c9d-9867-cf2484c40b18.png)

### convolution이란? 
- 만약 사진 한 장이 있다면, 그것은 가로폭(width), 세로폭(height), 그리고 색을 나타내는 R(빨강), G(초록), B(파랑)의 수치가 있을 것이다.
- softmax 함수를 적용하는 경우에는 모든 픽셀 정보를 입력으로 넣을 것이다.
- 그런데 convolution의 경우에는, 이미지의 매우 작은 부분 패치만 다룬다. 


![image](https://user-images.githubusercontent.com/15938354/175478511-8314e840-fb75-4674-9807-082900126862.png)

- 위의 예에서, 전체 이미지의 크기는 3x3x1이고 필터의 크기는 2x2x1이다.
- convolution은 필터를 사용해서 그 크기만큼 보고, 필터를 움직이면서 결국 전체 이미지를 본다. 

- 기본 신경망과 마찬가지로, 출력층 근처의 Layer에서는 Affine-ReLU를, 출력층에서는 Affine-Softmax를 사용한다. 
- 이미지 데이터의 경우, 가로*세로*채널(색상)으로 구성된 3차원 데이터이다. Fully Connected Layer에 데이터를 input하기 위해서는, 1차원으로 데이터를 평탄화 해야한다.
- 그러나, 이미지 같은 3차원 형상에서는 인접한 픽셀 값이 유사하고 먼 픽셀 값은 


### 패딩(padding)
- 패딩은 합성곱 연산 전에 입력 데이터 주변에 특정 값을 채우는 것을 말한다.
- 주로, 출력 데이터의 크기를 조정할 목적으로 사용한다.
