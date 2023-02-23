
## DataFrame Join
### Join이란?
- 두 개의 DataFrame을 합치는 것
- 열 기준 컬럼명으로 합치기 : merge

### 합치는 방법은?
- Inner : 두 DataFrame의 기준 컬럼에서 둘 다 존재하는 데이터만 Join
- Left Outer Join : 왼쪽 Dataframe으로 합치기
- Right Outer Join : 오른쪽 DataFrame으로 합치기
- Outer Join : 두 Dataframe의 모든 Data를 합치기 

#### Inner Join
- 두 DataFrame의 기준 컬럼에서 둘 다 존재하는 데이터만 Join함.

![image](https://user-images.githubusercontent.com/15938354/220836948-acf1568e-d8d2-4c7b-8957-1690dba05c27.png)

```python

pd.merge(left = DF1 , right = DF2, how = "inner", on = "이름")

```




https://programmerpsy.tistory.com/17
