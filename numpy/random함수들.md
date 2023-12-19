

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
