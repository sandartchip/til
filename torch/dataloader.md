

```python
from torch.utils.data import Dataset, DataLoader
```

- 파이토치에서 지원하는 기능.
- 파이토치의 도메인 특화 라이브러리들은 (FashionMNIST와 같은) 다양한 미리 준비해둔(pre-loaded) 데이터셋을 제공한다.
- 데이터셋은, torch.utils.data.Dataset의 하위 클래스로, 개별 데이터를 특정하는 함수가 구현되어 있다.
- 이러한 데이터셋은, 모델을 만들어보고(prototype) 성능을 측정(benchmark)하는 데 사용할 수 있다.
- 예시 데이터셋 : https://pytorch.org/vision/stable/datasets.html
 

- Dataset은 샘플과 정답(label)을 저장함
- DataLoader는 Dataset을 샘플에 쉽게 접근할 수 있도록, 순회 가능한 객체(iterable)로 감싼다.

- 데이터셋은, torch.utils.data.Dataset의 



https://tutorials.pytorch.kr/beginner/basics/data_tutorial.html
