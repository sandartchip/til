
# Reshape the image data into rows

```python
X_train = np.reshape(X_train, (X_train.shape[0], -1)) # (5000, 32, 32, 3) -> (5000, 3072)   (10000, 32, 32, 3) -> (500, 3072)
X_test = np.reshape(X_test, (X_test.shape[0], -1)) # -1은 numpy가 전체 element를 주어진 dimension에 맞게 나눔.
```

