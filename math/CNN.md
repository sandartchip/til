## 필터(Kernel)
#### 필터의 예시
-  소벨 필터
![image](https://user-images.githubusercontent.com/15938354/217469320-cfbabb13-7592-4155-8db7-d9b12adf871a.png)

- 원본 이미지에 위의 필터를 차례대로 적용시키면 가로선, 세로선 feature를 뽑아낼 수 있음. 

- 흑백 이미지의 

# CNN의 학습
- CNN은 필터을 학습한다.

## Featuer Map 
- 각각의 특징들을 패턴으로 읽어내는 것이 목적임.
- 입력으로부터 필터(커널)을 사용하여 합성곱을 취한 결과

![image](https://user-images.githubusercontent.com/15938354/217470269-b9bd9486-7f7c-463f-bc16-3b0d03d5a9a0.png)



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
- 바꾸지 않는 이유: Backbone이 맞아야 함. Pre-trained 모델을 사용하기 위해서임. pre-trained된 거에 transfer learning을 함. 
- Big data로 만든걸 가져 와서, 우리가 만든 Classifier를 붙여 줌. 
