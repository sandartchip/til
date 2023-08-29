
# Reshape the image data into rows

```python
X_train = np.reshape(X_train, (X_train.shape[0], -1)) # (5000, 32, 32, 3) -> (5000, 3072)   (10000, 32, 32, 3) -> (500, 3072)
X_test = np.reshape(X_test, (X_test.shape[0], -1)) # -1은 numpy가 전체 element를 주어진 dimension에 맞게 나눔.
```

- 열에 -1이 있으면 행에 따라 열의 갯수가 정해지고, 행에 -1이 있으면 열에 따라 행의 갯수가 정해 짐.

### 예시
```python
x = np.arange(12).reshape(3, 4)
Out[4]:
array([[ 0, 1, 2, 3],
        [ 4, 5, 6, 7],
        [ 8, 9, 10, 11]])


x.reshape(-1, 2)
-> shape(6, 2)

x.reshape(4, -1)
-> shape(4, 3)

```
