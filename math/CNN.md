

## CNN 종류
- AlexNet
- VGG
- ResNet
- GoogleNet
- EfficientNet

등등...
- ResNet50이 가장 기본이 되는 모델.

- torchvision에서는 이미 모델이 다 구현이 되어 있음.

```python
import torchvision.models as models

resnet50_32x4d = models.resnet50_32x4d()
alexnet = models.alexnet()
```

- 한 줄만 쓰면 사용 가능
- 실전에서 모델을 바꿔서 아용할 경우는 거의 없음. 
- Backbone이 맞아야 
