

- kNN예제 풀 때 k-Fold validation을 할 때, concatenate가 사용되었는데 axis가 햇갈림.....

##### 2차원 배열

```python
A2 = np.array([ [1,2,3], [10, 20, 30] ])
B2 = np.array([ [4,5,6], [40,50,60] ])
```

<img src="https://github.com/sandartchip/TIL/assets/15938354/0c9ee61b-ea13-4689-9b98-232404b0d953" width="150px">

```
np.concatenate((A2, B2), axis=0)
```

- 2차원 배열에서 axis=0은 행(위->아래) 방향을 의미함. concatenate와 같이 연결. 
##### result
```
array([[ 1, 2, 3],
       [10, 20 ,30],
      [4, 5, 6],
      [40, 50, 60]])
```

```python
np.concatenate((A2, B2), axis=1)
```

- 2차원 배열에서 axis=1은 열(왼->오른) 방향을 의미함.

#### result
```
>> array([[1, 2, 3, 4, 5, 6]
          [10, 20, 30, 40, 50, 60]])
```
