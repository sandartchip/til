
### Hidden Markov Model
![image](https://user-images.githubusercontent.com/15938354/167157178-2284abc0-afba-48cc-a269-debec6a61137.png)

### A
-State Transition Matrix : hidden state가 서로 전환될 확률. Hidden State Transition Matrix라고 생각하면 된다. 

### B
-emission probability Matrix

![image](https://user-images.githubusercontent.com/15938354/167160770-960858be-5035-42e8-8f7a-d0a61a571966.png)
- hidden state가 주어졌을 때 어떤 관측치를 보일 것인지 추측하는 확률.
- 각 observable state는 hidden state에 종속되어 있음. 
- b31 : Hidden State 1에 Observable state 3가 종속될 확률. 

### π
![image](https://user-images.githubusercontent.com/15938354/167161867-b7ee17a6-3615-428f-addc-ed01a168372c.png)
- 각 hidden state의 초기 확률.
- ex) state에 비, 해, 눈이 있으면 처음에 비가 올 확률, 해가 뜰 확률, 눈이 올 확률을 말한다.


### 2. Decoding 
- 모델(파라미터)이 주어지고, Observable sequence가 주어졌을 때, 각 시점에서의 hidden state 를 예측하는 것. 
- 이걸 찾는방법: Viterbi algorithm 

- ex. 정박사가 오늘 산책, 내일 산책, 글피 쇼핑했다면, 각 날들의 날씨는?
- O = (o1=산책, o2=산책, o3=연구 o4=쇼핑)이 주어졌을 때, Find the hidden state


https://www.youtube.com/watch?v=P02Lws57gqM
