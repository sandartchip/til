
- cs231n) 1-3. Softmax를 구현해야 함.
- 이 과제에서의 Softmax() 함수는 단지 softmax 함수 만이 아니라, 실제 모델 예측을 하기 위해 1개의 순전파 Layer과 연결되어 있는 softmax 함수이다.

- Softmax 함수의 forward, backward를 구현, Stochastic Gradient Desecent를 구현
- 소프트맥스 함수의 출력은 분류하고자 하는 클래스의 갯수만큼 차원을 가지는 벡터

- 개념이 너무 안잡혀 있어서 다시 정리 해 봄 ㅠㅠ

# 순전파
<img src="https://github.com/sandartchip/TIL/assets/15938354/72924510-72f0-439d-8698-9a6b3b295c69" width="180px" style="border: 1px solid #000"/>
- 수식 
- 행렬의 곱.

```python
scores = np.dot(X[i], W) # shape: 1 x D 
y_score = scores[y[i]]  # i번째 데이터의 정답 클래스의 점수 
result = np.log(np.exp(y_score) / np.sum(np.exp(scores)))  # scores의 각 원소들 exp하고 더함 
```

- Y = np.dot(X, W) + B
<img src="https://github.com/sandartchip/TIL/assets/15938354/2ef3eb3a-5e92-4463-b969-96135e585fd1" width="350px" />

- Affine 변환 이라고도 함.

### Softmax 함수의 Loss Function
<img src="https://github.com/sandartchip/TIL/assets/15938354/ef223aca-c3fc-45ab-bb33-f94df5747c5f" width="400px" />

#### Log 변환 
- 마지막 Probability 값에 Log값이 씌워 짐. 
<img src="https://github.com/sandartchip/TIL/assets/15938354/5a5c69c7-9bf0-4fd2-b082-a30a479cba8d" width="300px" />
<br>
- 각 class의 점수를 확률 분포를 적용해 계산하여 확률값으로 변환했을 때, 확률값이 1에 가까우면 가까울 수록 좋은 것.<br>
- 분류기 함수 f를 평가해주는 loss값은 적으면 적을 수록 좋은거. <br>
- 적으면 적을 수록 좋음의 분포를 나타내는 함수 = -log() 


# 역전파

#### 역전파-Softmax 계층
<img src="https://github.com/sandartchip/TIL/assets/15938354/e74ba827-5f27-42b7-9a91-bf650010f6d5" width="400px" />


#### Softmax - Cross Entropy Loss 전체 역전파 
##### 전체 모식도 
<img src="https://github.com/sandartchip/TIL/assets/15938354/fcb685ae-4867-41a1-a705-7c66ecb24e1a" width="600px" />

##### 전체모식도-축약도 (Softmax 뒤에 Cross Entropy가 붙음. 그래야 미분이 쉬워서)
<img src="https://github.com/sandartchip/TIL/assets/15938354/85f396d8-997c-4032-bfc3-48538841af56" width="350px" />


- 결국 **Softmax-Cross Entropy-with-Loss 계층의 최종적인 미분값은 yi-ti**임
- 이렇게 간단하게 최종 미분값이 계산될 수 있는 이유는 **손실함수로 크로스 엔트로피(CEE)를 사용하기 때문**임.  

- dW는 backpropagation을 이용하여 각 correct_class에서 Xi만큼 뺌 


<img src="https://github.com/sandartchip/TIL/assets/15938354/46970f47-01f6-48c9-b445-f4765f8938dd" />



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




https://ratsgo.github.io/deep%20learning/2017/10/02/softmax/ <br>
https://lionkingchuchu.tistory.com/38  <br>
https://jason7406.medium.com/cs231n-2-loss-functions-and-optimization-2-489b86404a13
