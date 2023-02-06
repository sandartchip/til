

## CNN 종류
- AlexNet
- VGG
- ResNet
- GoogleNet
- EfficientNet
등등...

- ResNet50이 가장 기본이 되는 모델.
- torchvision에서는 이미 모델이 다 구현이 되어 있음.
- 

```python
import torchvision.models as models

resnet50_32x4d = models.resnet50_32x4d()
alexnet = models.alexnet()
```

- 한 줄만 쓰면 사용 가능
- 실전에서 모델을 바꿔서 아용할 경우는 거의 없음. 
- 바꾸지 않는 이유: Backbone이 맞아야 함. Pre-trained 모델을 사용하기 위해서임. pre-trained된 거에 transfer learning을 함. 
- Big data로 만든걸 가져 와서, 우리가 만든 Classifier를 붙여 줌. 
