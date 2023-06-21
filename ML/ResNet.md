## down sampling과 채널 수
- down sampling과 채널 수 reduction은 **같은 게 아님**
- down sampling을 채널 수 reduction이랑 자꾸 햇갈려서 혼돈이 오는 중.
- 채널 수 reduction은 1x1 conv로 하는거임. downsampling은 max pooling이나 stride=2로 하는 겅미. 

- 둘이 동시에 일어날 수는 있지만, 이미지 처리의 다른 측면 임.
- down sampling은 각 Layer의 첫 번째 블록의 3x3 conv에서만 일어 남. 
- 채널 수는 각 Layer의 모든 블록에서 증가(1x1)했다가 그대로(3x3)였다가 감소(두번째 1x1)함. 

#### down sampling
<img src="https://github.com/sandartchip/TIL/assets/15938354/cae731a3-7ac2-41ce-9481-8b486630c71c" width="300px"/>

- 더 작은 이미지로 크기를 축소시키는 것.
- Max pooling, stride로 순회하는 거 같은거.

#### reducting the number of channel
- 이미지의 채널 갯수를 줄이는 거.
- 224x224픽셀 이미지가 RGB 채널 가지고 1000x1000 픽셀 이미지가 RGB 채널 가지듯.

- RGB(3개의 채널)->흑백(GrayScale, 1개의 채널) 이런 식으로, 특징 잡아내는 필터 갯수 줄이는거. 

![image](https://github.com/sandartchip/TIL/assets/15938354/3e43de92-26ff-4aba-8825-b68d7acd0d50)

- 이건 채널 갯수 줄이는거. RGB에서 흑백이 되는 거 처럼.
- downsampling 아님욬...

## 필터의 개념

<img src="https://github.com/sandartchip/TIL/assets/15938354/71a7f8b7-6680-49f5-a3f4-b840a7f20886" width="400px"/>

## 1x1 convolution의 역할
<img src="https://github.com/sandartchip/TIL/assets/15938354/6314365f-4fd1-4b82-9108-d1ad569734af" width="600px"/>

- 내가 자꾸 햇갈리는게, 인풋 이미지 크기와 필터 크기(channel size).
- 인풋 이미지 크기 줄이는건 down sampling. 

## 현재 해야 하는 일

<img src="https://github.com/sandartchip/TIL/assets/15938354/38054fb7-4319-42f0-bdd9-c42c49f76f52" width="350px"/>
<img src="https://github.com/sandartchip/TIL/assets/15938354/2555e6c9-8416-4a0d-8ea5-5e504fe998d8" />

- Stage : 한 개의 downsampling block과 여러 개의 residual block으로 이루어져 있다.
- **Downsampling block** : Path A와 path B로 구성되며, 마지막에 두 path의 output을 더한다.
- Path A : 3개의 conv로 구성된 bottleneck 구조로, input size를 2배 줄이고 channel dim을 4배 늘린다.
- Path B: channel size만 Path A와 동일하게 늘리는 1x1 conv 하나로 구성되어 있다.
- Residual block은 downsampling block과 동일한 구조인데, 대신 stride=1로 설정하여 input size는 유지한다.
 

- ResNet50의 마지막 Layer(Layer4)의 마지막 Bottle Neck block의 output feature map 갯수을 수정 
- Grad CAM에 ResNet50의 conv5_x(layer4)의 Bottle Neck 3개 중 마지막 Bottle Neck가 들어감
- 이 Conv Layer의 conv 결과(output feature map)의 갯수 변경 
- ResNet50의 마지막 Conv Layer의 Feature map의 갯수 변경 = Feature map을 만드는 output 필터의 갯수(필터 채널의 수 X) 변경 = output channel 수 바꾸기

- 코드 상으론 이 부분

![image](https://github.com/sandartchip/TIL/assets/15938354/dbe1823c-9f35-4d94-81ca-41a3df1c0e00)

<img src="https://github.com/sandartchip/TIL/assets/15938354/637e69a5-e97e-430d-b4e4-ffbaf8b72011" />


![image](https://github.com/sandartchip/TIL/assets/15938354/18c37fcf-3d4f-42ba-877b-e36fa437cf48)

<br>


# ResNet50
- ResNet은 간단한 구조를 가지고,  참신한 아이디어로 현재까지도 많은 network에서 사용되고 있음.
![image](https://github.com/sandartchip/TIL/assets/15938354/da58a590-93a1-4ad1-a593-020e3d943618)

- 실선은 feature map의 가로 세로 해상도가 바뀌지 않는 경우
- 점선은 다운 샘플링으로 해상도가 바뀌는 경우임. 이전 단계의 feature map이 가로 세로 방향으로 절반씩 줄어듬.

### Motivation 
 
- ResNet이 나오기 전까지, 근방의 모델은 오직 깊은 모델, 즉 레이어를 많이/깊이 쌓아서 성능이 높은 모델을 고르는 데 치중됨.
- ResNet의 저자는 모델이 깊어질 수록 최적화에 멀어진다는 점에 주목함. 

##### Vanishing Gradient Problem
<img src="https://github.com/sandartchip/TIL/assets/15938354/08c5dbce-28b0-4bb6-bbed-2758b7bacd4e" width="500px"/>

- Vanishing Gradient Problem은 딥러닝 중 Backpropagation 시 발생되는 어려움이다.
- 간단히 말하면, 모델이 깊어질 수록 급격히 Gradient의 영향력이 줄어드는 현상이다.

### Residual Block(BottleNeck)
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
<img src="https://github.com/sandartchip/TIL/assets/15938354/1fc446f8-b01f-4216-a2b0-7f9d26807e8c" width="300px" />
(그림 안 정확. 한번 더 확인 필요)
- 각 레이어는 여러개의 블록으로 이뤄져 있고 각 블록은 1x1 3x3 1x1 conv와 batch norm, relu로 연결되어 있음.
- 여기서 downsampling은 각 레이어의 모든 블록에 적용되는게 아님. 각 레이어의 첫 번째 블록에만 적용 됨.
- 첫 번째 블록에서 모든 1x1, 3x3, 1x1 conv 레이어에 적용되는 것도 아님.
- 첫 번째 블록의 3x3 conv에만 적용됨
  
- down sampling이란, **더 작은 이미지로 크기를 축소**시키는 것.
- ResNet에서는 복잡도를 줄이기 위해 stride=2로 대체함.
- ResNet에서는 차원이 바뀌는 블록의 첫 번째 convolutional layer에서 stride를 2로 사용하여 feature map 크기(갯수가 아님)를 줄여 줌.
- BottleNeck에서 BottleNeck으로 넘어갈 때 downsampling을 추가해주어 채널 사이즈를 맞춰 줌.
- 밑에 downsample if문 부분은 내부에서 size 안맞을 때 사용 (이거 맞는지 확인 필요)
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

#### conv3
- bottlen


#### _make_layer함수
![image](https://github.com/sandartchip/TIL/assets/15938354/64468c2e-5d61-4ca5-aa63-8ad362e4b814)
<img src="https://github.com/sandartchip/TIL/assets/15938354/0f41224e-b503-4dc5-a2cb-34ce72890f4f" />
- 이 make_layer함수 얘에 있는 얘내는 1x1 이게 아님.. Bottle Neck 임.(햇갈리지 말 것) 즉 이 블록 하나하나에 1x1 3x3 1x1 이거 세트로 묶여있는 애들임..
- 블록 내 시작 layer, downsampling 필요 -> 이 부분이 저거 맨 위에 있는 블록. 밑에 둘이는 #동일 블록 반복 이부분.
- inplanes: input channel 갯수.


- 레지듀얼 블록 여러개 연결해주는 애.
- 블록에 1x1이랑 3x3이랑 1x1 이런 애들 들어있음. 
- conv2_x, conv3_x, conv4_x, conv5_x을 구현하며 각 층에 해당하는 block을 갯수에 맞게 생성 및 연결해주는 역할을 함.
- 한 레이어 당 블록을 몇 개 생성할건지는
```python

def resnet50(pretrained=False, progress=True, **kwargs):
  return _resnet('resnet50', Bottleneck, [3, 4, 6, 3], pretrained, progress, **kwargs)
```
여기서 정했음
- block은 ResNet50의 경우, BottleNeck block임. bottle neck block은 그..내가 아는 1x1, 3x3, 1,1 convolution 연결된 걔.



#### downsampling 
- downsample을 이용해서 연산이 이뤄질 수 있도록 사이즈를 맞춰 줌.
- 큰 단위 Layer 시작할 떄 1번째 Bottle Neck에서 down sampling을 하는데, 그걸 하는 거는 3x3 걔인거임. (3x3블록에서 stride 2로 적용) 얘는 이미지 크기 줄이는거임. 채널 크기는 그대로임. (맞나..)

```python

layers.append(block(self.inplanes, planes, stride, downsample, self.groups, self.base_width, previous_dilation, norm_layer))

for _ in range(1, blocks):
 layers.append(block(self.inplanes, planes, groups=self.groups, base_width=self.base_width, dilation=self.dilation, norm_layer=norm_layer)
 
```
- 요기서 사용한 block은 각각 BottleNeck 1개 임!!
- 첫 번재 BOTTLENECK 블록에만 stride2를 적용하는데, 그 stride2 적용되는 곳이

![image](https://github.com/sandartchip/TIL/assets/15938354/ddd64ebb-7eb5-4f80-9a31-0ee65936499f) 
- 블록 안에 있는 3개짜리 conv애들 중에 conv3x3에만 적용되는거임요.

- self.inplanes=64에서 self.inplanes= planes * block.expansion 으로 inplanes가 업데이트 됨.

<img src="https://github.com/sandartchip/TIL/assets/15938354/19a0ab32-84c0-48c9-8630-d1954452ffc0" />


#### BottleNeck Architecture 
<img src="https://github.com/sandartchip/TIL/assets/15938354/bed30c51-17c1-4ca7-94ac-e61b71c30a67" width="400px"/>
<img src="https://github.com/sandartchip/TIL/assets/15938354/381a66e3-1885-4777-b5b0-a1f5d6cdce84">

- 각 residual 함수 F에 관하여, 3개의 Bottle Neck Block으로 구현하게 됨.
- 3개의 layer는 1x1, 3x3, 1x1로 구성됨.
- 얘가 BottleNeck Block 1개임.
- 각각의 Residual Block은 conv, batch normalization, relu로 구성
- 마지막 layer에서 identity mapping
- Identity Mapping 시 Identity Mapping 후 ReLu를 적용함.

#### 1. conv1x1
- 채널갯수를 1/4로 압축함. (downsampling 아님)

#### 2. conv3x3
- 이 압축된 상태에서 3x3 convolution으로 추가 feature를 뽑아 냄.
- 이미지 크기 바뀌는 down sampling 

#### 3. conv1x1
- 다시 채널의 수를 4배(self.expansion) 늘려 줌.

이런 식으로 변수의 수를 줄이면서도 원하는 갯수의 feature를 뽑을 수 있도록 함. 


##### Batch Normalization 
- 처음 input을 normalize한 다음 CNN을 통과하면 normalize상태가 무너짐. 걔가 normal distribution을 따른다는 보장이 없음
- 그래서 한 번 더 Normalize해주는 것.

<img src="https://github.com/sandartchip/TIL/assets/15938354/1429e480-2dac-48ac-842f-3d6b0f13476e" width="500px">

- 중간중간에 Fully Connected 층을 통해서 나오는 값에 붙여 줌
- 그 과정을 batch별로(?) 수행


https://jisuhan.tistory.com/71<br>
https://inhovation97.tistory.com/39<br>
https://gaussian37.github.io/dl-concept-resnet/<br>
https://pseudo-lab.github.io/pytorch-guide/docs/ch03-1.html<br>
https://bo-10000.tistory.com/133
