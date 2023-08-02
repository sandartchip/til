


- 머신러닝 혹은 딥러닝 모델 할 때 데이터셋을 나누어 사용한다.
- 요즘에는 다음과 같은 비율로 사용함

- Training Set: Validation Set: Test Set: 60 : 20 : 20

![image](https://github.com/sandartchip/TIL/assets/15938354/ad9f9ae8-e725-43bf-a256-7af07a6b0b84)


#### Validation Set과 Test Set의 차이

- Validation set은 1 epoch(batch 여러 번) 돌 때마다 만들어지는 여러 모델들 각각에 적용되어 성능을 측정한다.
- 최종 모델을 선정하기 위해 사용한다. (1 epoch을 epoch 수만큼 돌리는 만큼)

```python

```

- 반면 Test Set은 최종 모델에 대해 
