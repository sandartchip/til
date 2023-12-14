```python

arr = np.array([[1, 2, 3], [4, 5, 6]])
```

```python
# 노가다로 2차원 배열 loop 
for row in range(0, arr.shape[0]):
  for col in range(0, arr.shape[1]):
	print(arr[row, col], end= ' ')
```

```python
# nditer로 루프 
it = np.nditer(arr, flags=['multi_index'])


while not it.finished:
  idx = it.multi_index
  print(arr[idx], end=" ")

  it.iternext() 

```

### 장점
- for문에 비한 장점 : 3, 4차원이 되어도 코드가 바뀌지 않음.
- for문은 차원이 올라갈 때마다 코드를 재수정해야 함. 



