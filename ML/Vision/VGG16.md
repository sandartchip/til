

## 전체 구조 
<img src="https://github.com/sandartchip/TIL/assets/15938354/ba0ceade-1d7a-4059-bdb5-19265b494ce2" width="600px">

![image](https://github.com/sandartchip/TIL/assets/15938354/4188e419-87a4-4deb-94a8-d37c4d4e041e)


![image](https://github.com/sandartchip/TIL/assets/15938354/2a963597-fc14-45ea-90ff-4072a4bec418)




## 장점
1. 결정 함수의 비선형성 증가
- 7x7 필터로 conv -> ReLU가 1번. 3x3 filer로 conv -> ReLU가 3번 -> 비선형 함수가 더 많이 사용됨.
따라서 레이어가 증가함에 따라 비선형성이 증가하여 **모델 특징에 식별성이 증가**하게 된다.

2. 학습 파라미터 감소
- 파라미터 계산을 해보면 7x7 filter는 7x7 = 49개의 파라미터 사용, 3x3 filter는 3x3x3 = 27로 파라미터가 감소함. 

https://hayate1212.tistory.com/12
