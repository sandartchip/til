
- 데이터 프레임의 index는 중복 가능함.
- 내가 원하는 칼럼을 index로 만들 수 있다.
- inplace 파라미터는 원본 데이터에 덮어 씌울지를 물어보는것이다. 여기서는 inplace=True를 하였으므로, index가 바뀐 것을 원본에 바로 적용함.

```python
  exam.set_index(column, drop=True, inplace=True)
```

- 조회 시, 해당 인덱스에 해당하는 값을 모두 가지고 온다.
EXAMPLE
```python
 exam.set_index("class", inplace=True)
```
![image](https://user-images.githubusercontent.com/15938354/228199098-119e4703-e49c-4a78-ab3f-0a449cdc018c.png)



```python
  exam.loc[2]
```

![image](https://user-images.githubusercontent.com/15938354/228198842-0de0cd9e-33e7-43d8-b430-07fab794dae0.png)


https://gooopy.tistory.com/92
