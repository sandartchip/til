

```python

it = np.nditer(arr, flags=['multi_index'])


while not it.finished:
  idx = it.multi_index
  print(arr[idx], end=" ")

  it.iternext() 

```


- for문에 비한 장점 : 3, 4차원이 되어도 코드가 바뀌지 않음.
- for문은 차원이 올라갈 때마다 코드를 재수정해야 함. 
