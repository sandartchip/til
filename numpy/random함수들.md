

## randint 
- randint : input이 범위임. size 파라미터 붙이면 그게 output shape임.
- discrete uniform의 분포의 random 정수 생성.

```python
random.randint(1, 10)
>>> 5   (1~10 사이 정수 1개 )

np.random.randint(2, size=10)
>>> array([1, 0, 0, 0, 1, 1, 0, 0, 1, 0]) # random


np.random.randint(5, size=(2, 4))
>>>

```

## rand
- random.rand(m, n) : 0~1의 균일분포 표준정규분포 난수를 matrix array (m, n) 생성
  
## randn 
- random.randn(m, n) : 0~1 사이의 가우시안 표준 정규 분포에서 난수 matrix array 생성
- input으로 들어오는게 **matrix array shape임** 
- 표준 정규분포를 다음과 같이 표현 가능

```sigma * np.random.randn() + mu```

### 예시 

```python
3 + 2.5 * np.random.randn(2, 4)

>>
array([[-4.49401501,  4.00950034, -1.81814867,  7.29718677],   # random
       [ 0.39924804,  4.68456316,  4.99394529,  4.84057254]])  # random
```

https://numpy.org/doc/stable/reference/random/generated/numpy.random.randn.html
