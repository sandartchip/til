### 서론
-pandas에 대해 흔히들 갖고 잇는 오해가 pandas는 순차적으로 데이터를 조회하기 때문에, 데이터 전처리 속도가 매우 느리다는 것이다.
-이 말은 반은 맞고 반은 틀리다고 할 수 있는데, dataframe에서 특정 데이터를 단순하게 조회하면, 순서대로 하나하나 조회하기 때문에 속도가 매우 느려지고, 도리어 이 특징을 이용해서, 데이터 전처리 속도를 줄일 수도 있다.

- 그러나, 인덱스를 사용하여 조회를 하게 된다면, 순차적 조회가 아닌 한 번에 index에 해당하는 값을 가지고 오기 때문에 조회 속도가 아주 빨라진다.

### detail
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
