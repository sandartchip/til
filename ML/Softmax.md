
- cs231n) 1-3. Softmax를 구현해야 함.
- 이 과제에서의 Softmax() 함수는 단지 softmax 함수 만이 아니라, 실제 모델 예측을 하기 위해 1개의 Affine Layer과 연결되어 있는 softmax 함수이다.

- Softmax 함수의 forward, backward를 구현, Stochastic Gradient Desecent를 구현
- 소프트맥스 함수의 출력은 분류하고자 하는 클래스의 갯수만큼 차원을 가지는 벡터

- 개념이 너무 안잡혀 있어서 다시 정리 해 봄 ㅠㅠ

# 순전파
<img src="https://github.com/sandartchip/TIL/assets/15938354/72924510-72f0-439d-8698-9a6b3b295c69" width="180px" style="border: 1px solid #000"/>

```

- 행렬의 곱.
- 수식 


- Y = np.dot(X, W) + B
<img src="https://github.com/sandartchip/TIL/assets/15938354/2ef3eb3a-5e92-4463-b969-96135e585fd1" width="350px" />

- Affine 변환 이라고도 함.

# 역전파

- dW는 backpropagation을 이용하여 각 correct_class에서 Xi만큼 뺌 


## Softmax 함수의 입력으로 어떻게 바꿀까? 
<img src="https://github.com/sandartchip/TIL/assets/15938354/717a9e0b-09ca-41c1-aa60-a8e5461d3065">

##### 예시
- 4개의 독립변수 : 모델이 4차원 벡터를 입력으로 받음을 의미. 
- Softmax 함수의 입력으로 사용되는 벡터의 차원--(변형)--> 분류하고자 하는 클래스의 갯수 

- 데이터 값이 setosa라면, setosa의 원-핫 벡터는 [0 1 0]이다. 이 경우, 예측값과 실제값의 오차가 0이 되는 경우는 소프트맥스 함수의 결과가 [0 1 0] 이다.

- 가중치 연산을 통해 3차원 벡터로 변환한다.

<img src="https://github.com/sandartchip/TIL/assets/15938354/5281fa20-88e3-4f8c-a4ef-97fea115c624">

- 화살표(Input과 Output)는 총 (4x3 =12개)
- 전부 다른 가중치를 가지고, 학습 과정에서 점차적으로 **오차를 최소화하는 가중치로 값이 업데이트** 된다.

## 오차를 어떻게 구할까?
- Softmax 함수의 출력은 분류하고자 하는 클래스의 갯수만큼 차원을 가지는 벡터.
- 0과 1사이의 값.

<img src="https://github.com/sandartchip/TIL/assets/15938354/666bf01e-1caf-46e4-b1c5-5e33315bf4c5">

- Softmax의 결과와 One Hot으로 변형된 실제 레이블간의 오차를 계산(cross-entropy 함수)




https://ratsgo.github.io/deep%20learning/2017/10/02/softmax/
https://lionkingchuchu.tistory.com/38
