

```python
from torch.utils.data import Dataset, DataLoader
```

### Dataset과 DataLoader 

- 파이토치에서 지원하는 기능.
- 파이토치의 도메인 특화 라이브러리들은 (FashionMNIST와 같은) 다양한 미리 준비해둔(pre-loaded) 데이터셋을 제공한다.
- 데이터셋은, torch.utils.data.Dataset의 하위 클래스로, 개별 데이터를 특정하는 함수가 구현되어 있다.
- 이러한 데이터셋은, 모델을 만들어보고(prototype) 성능을 측정(benchmark)하는 데 사용할 수 있다.
- 예시 데이터셋 : https://pytorch.org/vision/stable/datasets.html
 

- Dataset은 샘플과 정답(label)을 저장함
- DataLoader는 Dataset을 샘플에 쉽게 접근할 수 있도록, 순회 가능한 객체(iterable)로 감싼다.

### 데이터셋 불러오기 
- TorchVision에서 Fashion-MNIST 데이터셋을 불러오는 예제.
- Fashion-MNIST는 Zalando의 기사 이미지 데이터셋으로, 60,000개의 학습 예제와 10,000 개의 테스트 예제로 이루어져 있다.
- 각 예제는 흑백(28x28)의 이미지와 10개 분류(class) 중 하나인 정답(label)로 구성된다.


### Example - Fashion MNIST 

```python

import torch
from torch.utils.data import Dataset
from torchvision import datasets
from torchvision.transforms import ToTensor
import matplotlib.pyplot as plt


training_data = datasets.FashionMNIST(
 root='data', # 학습/테스트 데이터가 저장되는 경로.
 train=True,  # 학습용 또는 테스트용 데이터셋 여부를 지정 
 download=True, # 데이터가 없는 경우, 인터넷에서 다운로드.
 transform=ToTensor() # 특징(feature)과 정답(label) 변형(transform)을 지정.
)

```




https://tutorials.pytorch.kr/beginner/basics/data_tutorial.html
