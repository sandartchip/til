

### np.argsort
##### 오름차순 정렬
```python
a = np.array([1.5, 0.2, 4.2, 2.5])
s = a.argsort()

print(s)  
-> [1 0 3 2]

print(a[s])
-> [0.2, 1.5, 2.5, 4.2]
```

<img src="https://github.com/sandartchip/TIL/assets/15938354/d07933d3-a729-4e2e-bd0f-9e0ab232b28a" width="300px" />


```a.argsort()```는 어레이 a를 정렬하는 인덱스의 어레이 [1 0 3 2]를 반환함.

a[s]와 같이 인덱스의 어레이 s를 사용해서 어레이 a를 다시 정렬하면, 오름차순으로 정렬된 어레이 [0.2, 1.5, 2.5, 4.2]가 됨. 

##### 내림차순 정렬

a[a.argsort()[::-1]]

-> index array를 뒤집은 후 정렬에 사용

a[a.argsort()][::-1]
-> 오름차순 sort된 array를 다시 뒤집음. 



#### 참고자료 
https://codetorial.net/tips_and_examples/numpy_argsort.html
