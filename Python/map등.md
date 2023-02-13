

## map() 함수

- map() 함수는 목록, 튜플 등과 같은 특정 반복 가능한 객체의 모든 요소에 함수를 적용하는 데 사용된다.

```python

def fn(a):
    return 10 * a

lst = [1, 2, 3, 4]

ans = list(map(fn, lst))
print(ans)

```
