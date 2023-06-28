


## Validation Loss가 안 줄어들 경우

### 1. 데이터 전처리 
- 데이터를 표준화하고 정규화하자. (Batch Norm, Scaling)

### 2. 모델 강제성 
- 모델이 너무 복잡한지 확인하자. dropout을 추가하고 각 계층의 layer 수 또는 뉴런 수를 줄임.

### 3. 학습 속도 및 감소 속도 
- 학습 속도를 줄이자.
- 학습을 하기에 좋은 시작 값은 보통 0.0005에서 0.001 사이임.
- 또한 1e-6의 decay rate를 고려하자. 

https://sulung-sulung.tistory.com/18
