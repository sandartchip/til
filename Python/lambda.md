

- lambda 인자: 표현식

```python
def add(x, y):
   return x+y
```

다음 함수를 
```python
add = lambda x, y: x+y
```

으로 변형 가능 

### 사용 예시

```python
mylist = [1, 2, 3, 4, 5]

mylist2 = list(map(lambda x: x*2, mylist))

print(mylist)
```

> 출력결과 [2, 4, 6, 8, 10]
