![image](https://github.com/sandartchip/TIL/assets/15938354/9809b743-e62a-47cc-990b-7d3a42fc181a)

- axis=0은 행 방향
- axis=1은 열 방향

```python
df = pd.DataFrame(
    {'name': ['KIM', 'LEE', 'SMITH','BROWN', 'MILLER'],
     'age': [24, 32, 43, 24, np.nan],
     'height': [178, 168, 171, 185, 176],
     'sex': ['M', 'F', 'F', 'M', 'F']})
df


"""
	name	age	height	sex
0	KIM	24.0	178	M
1	LEE	32.0	168	F
2	SMITH	43.0	171	F
3	BROWN	24.0	185	M
4	MILLER	NaN	176	F
"""
```


### ex1) drop(axis=0)

df.drop([1, 2], axis=0)

-> 세로 index 1, 2가 없어짐

"""
	name	age	height	sex
0	KIM	24.0	178	M
1	LEE	32.0	168	F
2	SMITH	43.0	171	F
3	BROWN	24.0	185	M
4	MILLER	NaN	176	F
"""

### ex2) drop(axis=1)
df.drop(['age', 'height'], axis=1) -> 가로방향의 age, height 컬럼 제거 

"""
	name	sex
0	KIM	M
1	LEE	F
2	SMITH	F
3	BROWN	M
4	MILLER	F
"""


https://hogni.tistory.com/49
