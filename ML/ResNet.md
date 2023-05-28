

### ResNet50
- Residual Net
- 각각의 Convolution -> Batch Normalization -> ReLu로 묶인 블럭 별로
Residual 값을 추가적으로 더해줌으로써 Gradient Vanishing/Exploding 문제를 해결할 수 있다.

- Batch Normalization : 처음 input을 normalize한 다음 CNN을 통과하면 normalize상태가 무너짐. 걔가 normal distribution을 따른다는 보장이 없음
- 그래서 한 번 더 Normalize해주는 것.

<img src="https://github.com/sandartchip/TIL/assets/15938354/1429e480-2dac-48ac-842f-3d6b0f13476e" width="500px">

- 중간중간에 Fully Connected 층을 통해서 나오는 값에 붙여 줌
- 그 과정을 batch별로(?) 수행
