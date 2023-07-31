
```python
 outputs = model(inputs) # 순전파
 pred = nn.Softmax(dim=1)(outputs)
```

- 그냥 모델만 통과시키면, Score(Logit)이 나옴. 얘는 그냥 음수도 나올 수 있고.. 아무 값이나 나올 수 있음. 
- 해당 output tensor에 softmax를 적용시키면, output tensor는 Input Tensor와 같은 shape에, (dim이 1인 경우, 가로가) 모든 값들은 sum값이 1이 됨.


- batch size 16인 경우 위는 model 통과시킨 결과, 아래는 softmax 통과 시킨 결과.

![image](https://github.com/sandartchip/TIL/assets/15938354/f0feda5d-7050-4958-91b9-c229ad8f4c17)


https://velog.io/@olxtar/nn.Softmax
