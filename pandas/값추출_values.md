

 - numpy representation of Dataframe 을 리턴함.


```python
df = pd.DataFrame({'age':    [ 3,  29],
                   'height': [94, 170],
                   'weight': [31, 115]})
```

df
   age  height  weight
0    3      94      31
1   29     170     115

df.dtypes
age       int64
height    int64
weight    int64
dtype: object
df.values
array([[  3,  94,  31],
       [ 29, 170, 115]])
