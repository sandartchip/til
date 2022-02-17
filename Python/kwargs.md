
### kwargs 

```
def print_param2(**kargs):
  
  for name, value in kwargs.items():
    print ("%s : %s") % (name, value)

print_param2(first='a', second'b', third='c', fourth='d')
```

- 파라미터명을 같이 보낼 수 있다.
- kwargs는 딕셔너리 형태로 전달된다.
