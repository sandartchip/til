## 필터의 개념

<img src="https://github.com/sandartchip/TIL/assets/15938354/71a7f8b7-6680-49f5-a3f4-b840a7f20886" width="400px"/>



## 현재 해야 하는 일

<img src="https://github.com/sandartchip/TIL/assets/15938354/38054fb7-4319-42f0-bdd9-c42c49f76f52" width="350px"/>

- Grad CAM에 ResNet50의 conv5_x(layer4)의 Bottle Neck 3개 중 마지막 Bottle Neck가 들어감
- 이 Conv Layer의 conv 결과(output feature map)의 갯수 변경 
- ResNet50의 마지막 Conv Layer의 Feature map의 갯수 변경 = Feature map을 만드는 output 필터의 갯수(필터 채널의 수 X) 변경 = output channel 수 바꾸기

- 코드 상으론 이 부분
![image](https://github.com/sandartchip/TIL/assets/15938354/dbe1823c-9f35-4d94-81ca-41a3df1c0e00)


![image](https://github.com/sandartchip/TIL/assets/15938354/18c37fcf-3d4f-42ba-877b-e36fa437cf48)

<img src="https://github.com/sandartchip/TIL/assets/15938354/a963b250-c33e-440a-aee9-0e7604cc1bce" width="300px" />
<br>
<img src="https://github.com/sandartchip/TIL/assets/15938354/6314365f-4fd1-4b82-9108-d1ad569734af" width="600px"/>


- 내가 자꾸 햇갈리는게, 인풋 이미지 크기와 필터 크기(channel size).
- 인풋 이미지  

# ResNet50
- ResNet은 간단한 구조를 가지고,  참신한 아이디어로 현재까지도 많은 network에서 사용되고 있음.
- ![image](https://github.com/sandartchip/TIL/assets/15938354/a8cfbe7c-9f13-4300-b38b-b3e1e08022f2)
- stride2의 downsampling이 각 Residual 블록에서 적용됨. 


### Motivation 
 
- ResNet이 나오기 전까지, 근방의 모델은 오직 깊은 모델, 즉 레이어를 많이/깊이 쌓아서 성능이 높은 모델을 고르는 데 치중됨.
- ResNet의 저자는 모델이 깊어질 수록 최적화에 멀어진다는 점에 주목함. 

##### Vanishing Gradient Problem
<img src="https://github.com/sandartchip/TIL/assets/15938354/08c5dbce-28b0-4bb6-bbed-2758b7bacd4e" width="500px"/>

- Vanishing Gradient Problem은 딥러닝 중 Backpropagation 시 발생되는 어려움이다.
- 간단히 말하면, 모델이 깊어질 수록 급격히 Gradient의 영향력이 줄어드는 현상이다.

### Residual Net
<img src="https://github.com/sandartchip/TIL/assets/15938354/34c5227a-ad2f-45a7-8a01-ca3755900f30" width="500px"/>

- ResNet 모델에 사용되는 가장 기본적인 구조.
- BottleNeck Architecture(Residual Block)이라고 불림.
- 같은 input, output을 취함.
``` input:x, output: relu(F(X)+x) ```

- 이렇게 구조를 띈 layer는 입력값이 출력으로 그대로 더해지는 short 구조를 취하게 됨. 
- 입력 값이 출력값에 들어감에 따라, 레이어들이 많아지면서 잊혀지는 vanishing gradient problem을 해결하게 됨.

#### ResNet50 Layers
![image](https://github.com/sandartchip/TIL/assets/15938354/bbc3c129-fac0-4169-8b88-45053c7674c3)


- ResNet50인 이유? 1+1+ 9+12+18+9 = 50
- 총 50개의 layer를 갖고 있으며, 각각의 conv 청크에 있는 []가 residual Block임을 명시해 줌.
- Layer마다 다른 Residual Block 형태가 반복되어 학습되는 과정을 거침.

#### convolution Block 
<img src="https://github.com/sandartchip/TIL/assets/15938354/dad341d8-6637-4e97-bd2f-28b9c869f1b1">


#### expansion
- in_planes는 input data의 채널 수 이고, out_planes는 output data의 채널 수임.
- <img src="https://github.com/sandartchip/TIL/assets/15938354/64825026-8bc0-4036-9e54-91ee9283c254" />

#### 필터
- 필터의 개수는 각 block 들을 거치면서 증가함 (64->128->

#### inplanes
- input channel의 갯수.
- ResNet50에서 inplanes(input feature map size)는 64으로 초기화되어 있음.
- 이후에 컨볼루션 레이어를 거치면서 채널의 갯수는 늘어남. 

#### Down Sampling
- down sampling이란, **더 작은 이미지로 크기를 축소**시키는 것.
- ResNet에서는 복잡도를 줄이기 위해 stride=2로 대체함.
- ResNet에서는 차원이 바뀌는 블록의 첫 번째 convolutional layer에서 stride를 2로 사용하여 feature map 크기를 줄여 줌.
- 따라서 conv3 1, con4 1, conv5 1에서 사용됨. (틀린 거 아님?)

## code로 구현
- BottleNeck 여러 개 연결 

<img src="https://github.com/sandartchip/TIL/assets/15938354/471ed494-588e-4901-9d64-a10246fbb4e5" />

<img src="https://github.com/sandartchip/TIL/assets/15938354/186495ab-fcb6-4967-84c8-2f3a3c841558" />

#### 전체 구조 - code

- 처음에 BottleNeck에 들어가기 전 부분. 
<img src="https://github.com/sandartchip/TIL/assets/15938354/ab7c1415-558e-482c-bf8f-4376959bcafe" />
<img src="https://github.com/sandartchip/TIL/assets/15938354/1e736c20-a702-4e9e-8eea-cd16267e8f16" />

### 전체 ResNet
![image](https://github.com/sandartchip/TIL/assets/15938354/ffecbed4-6e2b-450f-8d26-308a9e157231)

#### _make_layer함수
![image](https://github.com/sandartchip/TIL/assets/15938354/64468c2e-5d61-4ca5-aa63-8ad362e4b814)
- conv2X, conv3_x, conv4_x, conv5_x을 구현하며 각 층에 해당하는 block을 갯수에 맞게 생성 및 연결해주는 역할을 함.

- self.inplanes=64에서 self.inplanes= planes * block.expansion 으로 inplanes가 업데이트 됨.


#### BottleNeck Architecture 
<img src="https://github.com/sandartchip/TIL/assets/15938354/bed30c51-17c1-4ca7-94ac-e61b71c30a67" width="400px"/>
<img src="https://github.com/sandartchip/TIL/assets/15938354/381a66e3-1885-4777-b5b0-a1f5d6cdce84">

- downsample을 이용해서 연산이 이뤄질 수 있도록 사이즈를 맞춰 줌.


- 각 residual 함수 F에 관하여, 3개의 Bottle Neck Block으로 구현하게 됨.
- 3개의 layer는 1x1, 3x3, 1x1로 구성됨.
- 얘가 BottleNeck Block 1개임.
- 각각의 Residual Block은 conv, batch normalization, relu로 구성
- 마지막 layer에서 identity mapping
- Identity Mapping 시 Identity Mapping 후 ReLu를 적용함.

##### 1. conv1x1
- 


##### Batch Normalization 
- 처음 input을 normalize한 다음 CNN을 통과하면 normalize상태가 무너짐. 걔가 normal distribution을 따른다는 보장이 없음
- 그래서 한 번 더 Normalize해주는 것.

<img src="https://github.com/sandartchip/TIL/assets/15938354/1429e480-2dac-48ac-842f-3d6b0f13476e" width="500px">

- 중간중간에 Fully Connected 층을 통해서 나오는 값에 붙여 줌
- 그 과정을 batch별로(?) 수행


https://jisuhan.tistory.com/71
