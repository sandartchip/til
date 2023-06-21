

# ResNet50
- ResNet은 간단한 구조를 가지고,  참신한 아이디어로 현재까지도 많은 network에서 사용되고 있음. 

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
<img src="https://github.com/sandartchip/TIL/assets/15938354/372360b1-3291-4afc-924c-9deccebf41b7" width="700px"/>
- 1+1+ 9+12+18+9 = 50
- 총 50개의 layer를 갖고 있으며, 각각의 conv 청크에 있는 []가 residual Block임을 명시해 줌.


<img src="https://github.com/sandartchip/TIL/assets/15938354/bed30c51-17c1-4ca7-94ac-e61b71c30a67" width="700px"/>

#### 필터
- 필터의 개수는 각 block 들을 거치면서 증가함 (64->128->

#### inplanes
- input channel의 갯수.
- ResNet50에서 inplanes는 3으로 초기화되어 있음.
- ResNet50은 맨 처음에 3개의 채널의 input을 받는다는 얘기.
- 이후에 컨볼루션 레이어를 거치면서 채널의 갯수는 늘어남. 

#### Down Sampling
- down sampling이란, 더 작은 이미지로 크기를 축소시키는 것.
- ResNet에서는 복잡도를 줄이기 위해 stride=2로 대체함.
- ResNet에서는 차원이 바뀌는 블록의 첫 번째 convolutional layer에서 stride를 2로 사용하여 feature map 크기를 줄여 줌.
- 따라서 conv3 1, con4 1, conv5 1에서 사용됨. 

#### code로 구현
- 각 residual 함수 F에 관하여, 3개의 Layer stack으로 구현하게 됨.
- 3개의 layer는 1x1, 3x3, 1x1로 구성됨. 

##### BottleNeck Architecture 
- 각 residual 함수 F에 관하여, 3개의 Layer stack으로 구현하게 됨.
- 3개의 Layer는 1x1, 3x3, 1x1 convolutional layer로 이루어짐.

- 각각의 Convolution -> Batch Normalization -> ReLu로 묶인 블럭 별로
Residual 값을 추가적으로 더해줌으로써 Gradient Vanishing/Exploding 문제를 해결할 수 있다.

- Batch Normalization : 처음 input을 normalize한 다음 CNN을 통과하면 normalize상태가 무너짐. 걔가 normal distribution을 따른다는 보장이 없음
- 그래서 한 번 더 Normalize해주는 것.

<img src="https://github.com/sandartchip/TIL/assets/15938354/1429e480-2dac-48ac-842f-3d6b0f13476e" width="500px">

- 중간중간에 Fully Connected 층을 통해서 나오는 값에 붙여 줌
- 그 과정을 batch별로(?) 수행


https://jisuhan.tistory.com/71
