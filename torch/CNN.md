![image](https://user-images.githubusercontent.com/15938354/175475132-66f3ee6d-c341-47ea-95c7-e54ae5debe2e.png)


이미지를 입력으로 받고, convolution을 해서 feature map들을 얻는다.

subsampling을 한 뒤 linear layer로 이어져서, classification을 수행한다.


![image](https://user-images.githubusercontent.com/15938354/175477871-81f8bde5-2cb3-4c9d-9867-cf2484c40b18.png)

### convolution이란? 
- 만약 사진 한 장이 있다면, 그것은 가로폭(width), 세로폭(height), 그리고 색을 나타내는 R(빨강), G(초록), B(파랑)의 수치가 있을 것이다.
- softmax 함수를 적용하는 경우에는 모든 픽셀 정보를 입력으로 넣을 것이다.
- 그런데 convolution의 경우에는, 이미지의 매우 작은 부분 패치만 다룬다. 


![image](https://user-images.githubusercontent.com/15938354/175478511-8314e840-fb75-4674-9807-082900126862.png)
