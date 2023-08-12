

## hstack
- 2차원일 때 두 번째 axis로 concatenate(axis=1) 이랑 똑같음요
- 옆으로 붙이는 거

```python
a = np.array((1, 2, 3))
b = np.array((4, 5, 6))

np.hstack((a, b))
```
>>> array([1, 2, 3, 4, 5, 6])


```python
a = np.array([[1], [2], [3]])
b = np.array([[4], [5], [6]])

생긴거

[[1],
 [2],
 [3]]

[[4],
 [5],
 [6]]
np.hstack((a, b)) -> 옆으로 붙임.
```

>>>
>>>[[1, 4],
   [2, 5],
   [3, 6]]

