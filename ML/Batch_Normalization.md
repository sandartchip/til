


![image](https://github.com/sandartchip/TIL/assets/15938354/c61bef61-ee09-4c59-8982-8cd4165b98df)



- 학습 데이터를 전부 넣어서 gradient를 구하고 그 모든 gradient를 평균해서 한 번에 모델 업데이트를 하면 부하가 큼
- 데이터를 batch 단위로 나눠서 학습 함




## Batch Normalization 

#### Stochastic Gradient Descent
![image](https://github.com/sandartchip/TIL/assets/15938354/96f84f18-eecb-4452-be95-c4fcd2f4682e)

- 1 epoch 당 전체 데이터를 한 번 학습 함
- Gradient를 구하는 단위를 Batch라고 함.


- SGD에서는 gradient를 한 번 업데이트하기 위하여 일부 데이터만을 사용함. 즉, batch size만큼 사용 함.

- 학습 과정에서 각 배치 단위 별로 데이터가 다양한 분포를 가지더라도 **각 배치별로 평균과 분산을 이용해 정규화 하는 것** 을 말함.

- 위 그림을 보면 batch 단위나 layer에 따라서 입력 값의 분포가 모두 다르지만, 정규화를 통하여 분포를 zero mean gaussian 형태로 만듬.
- 그러면 평균은 0, 표준 편차는 1로 데이터의 분포를 조정할 수 있음. 


https://gaussian37.github.io/dl-concept-batchnorm/
